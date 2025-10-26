```dataviewjs
// =============================
// 🔹 Pomodoros + TimeEntries detalhado (com ícones no horário e seletor estilizado)
// =============================
const root = dv.el("div", "");

const CONFIG = {
    tag: "#calendar/daily",      // Tag usada para filtrar notas
    sectionHeader: "Logs",       // Cabeçalho da seção alvo
    rangeDays: <% tp.system.prompt("Pomodoro rangeDays config")%>,               // Intervalo em dias (padrão: últimos 30)
    sortOrder: "desc"            // Opções: "asc" | "desc"
};
//-----------------------------------------------------
// 🗓️ INTERVALO DE DATAS
//-----------------------------------------------------
const endDate = moment('<% tp.date.now("YYYY-MM-DD") %>', 'YYYY-MM-DD');
const startDate = moment(endDate).subtract(CONFIG.rangeDays, 'days');

// -----------------------------
// 🔹 Captura Pomodoros (#calendar/daily)
let pomodoros = [];
for (let page of dv.pages("#calendar/daily").where(p => Array.isArray(p.pomodoros))) {
  for (let p of page.pomodoros) {
    let start = new Date(p.startTime);
    let end = new Date(p.endTime);
    if (isNaN(start) || start < startDate || start > endDate) continue;

    let duration = typeof p.plannedDuration === "number"
      ? p.plannedDuration
      : (!isNaN(end) ? (end - start) / 60000 : 0);

    pomodoros.push({
      start,
      end,
      duration,
      type: p.type ?? "—",
      source: "Pomodoro",
      file: page.file,
      created: page.file.ctime
    });
  }
}

// -----------------------------
// 🔹 Captura TimeEntries (#task)
let timeEntries = [];
for (let page of dv.pages("#task").where(p => Array.isArray(p.timeEntries))) {
  for (let te of page.timeEntries) {
    let start = new Date(te.startTime);
    let end = new Date(te.endTime);
    if (isNaN(start) || isNaN(end) || start < startDate || start > endDate) continue;

    let duration = (end - start) / 60000;
    timeEntries.push({
      start,
      end,
      duration,
      type: te.description ?? "—",
      source: "TimeEntry",
      file: page.file,
      created: page.file.ctime
    });
  }
}

// -----------------------------
// 🔹 Combina e ordena (por data inicial)
let sortAscending = false;
let combined = [...pomodoros, ...timeEntries].sort((a, b) => b.start - a.start);

// -----------------------------
// 📊 RESUMO
const totalMin = combined.reduce((acc, e) => acc + (e.duration || 0), 0);
const totalPom = combined.filter(e => e.source === "Pomodoro").length;
const totalTE = combined.filter(e => e.source === "TimeEntry").length;

const summaryDiv = document.createElement("div");
summaryDiv.style.cssText = `
  background: rgba(0,0,0,0.7);
  border-radius: 8px;
  padding: 12px;
  margin-bottom: 15px;
  border-left: 4px solid #7e57c2;
`;
summaryDiv.innerHTML = `
<div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(140px,1fr));gap:8px;margin-bottom:10px;">
  <div style="text-align:center;padding:8px;background:rgba(255,255,255,0.15);border-radius:6px;">
    <div style="font-size:0.8em;color:#e0e0e0;margin-bottom:4px;">📅 Período</div>
    <div style="font-weight:bold;font-size:0.9em;color:#fff;">${startDate.format("DD/MM")} → ${endDate.format("DD/MM")}</div>
  </div>
  <div style="text-align:center;padding:8px;background:rgba(255,255,255,0.15);border-radius:6px;">
    <div style="font-size:0.8em;color:#e0e0e0;margin-bottom:4px;">⏱️ Total</div>
    <div style="font-weight:bold;font-size:0.9em;color:#4caf50;">${Math.ceil(totalMin)} min</div>
  </div>
  <div style="text-align:center;padding:8px;background:rgba(255,255,255,0.15);border-radius:6px;">
    <div style="font-size:0.8em;color:#e0e0e0;margin-bottom:4px;">🍅 Pomodoros</div>
    <div style="font-weight:bold;font-size:0.9em;color:#ff9800;">${totalPom}</div>
  </div>
  <div style="text-align:center;padding:8px;background:rgba(255,255,255,0.15);border-radius:6px;">
    <div style="font-size:0.8em;color:#e0e0e0;margin-bottom:4px;">📝 TimeEntries</div>
    <div style="font-weight:bold;font-size:0.9em;color:#2196f3;">${totalTE}</div>
  </div>
</div>
`;
root.appendChild(summaryDiv);

// -----------------------------
// 🔹 Controles
const controls = document.createElement("div");
controls.style.cssText = `
  display:flex;
  justify-content:space-between;
  align-items:center;
  margin-bottom:12px;
  background:rgba(0,0,0,0.6);
  padding:8px;
  border-radius:6px;
`;

const label = document.createElement("span");
label.textContent = "Agrupar/Ordenar por:";
label.style.cssText = "color:#e0e0e0;font-size:0.9em;margin-right:8px;";

// 🔸 Seletor estilizado (fundo igual nas opções)
const sortSelect = document.createElement("select");
sortSelect.style.cssText = `
  background: rgba(60, 60, 60, 0.9);
  border: 1px solid rgba(255,255,255,0.2);
  border-radius: 4px;
  padding: 4px 8px;
  color: #fff;
  font-size: 0.9em;
  cursor: pointer;
  transition: background 0.25s ease;
`;
sortSelect.onmouseenter = () => sortSelect.style.background = "rgba(80,80,80,0.95)";
sortSelect.onmouseleave = () => sortSelect.style.background = "rgba(60,60,60,0.9)";

const options = [
  { value: "start", text: "⏰ Horário" },
  { value: "type", text: "🎯 Tipo/Descrição" },
  { value: "note", text: "🔗 Nota/Arquivo" }
];
options.forEach(opt => {
  const option = document.createElement("option");
  option.value = opt.value;
  option.textContent = opt.text;
  option.style.background = "rgba(60,60,60,0.9)";
  option.style.color = "#fff";
  sortSelect.appendChild(option);
});

// 🔄 Botão alternar
const toggleBtn = document.createElement("button");
toggleBtn.textContent = "🔄 Alternar ordem";
toggleBtn.style.cssText = `
  background: rgba(60,60,60,0.9);
  border: 1px solid rgba(255,255,255,0.2);
  border-radius: 4px;
  padding: 4px 8px;
  color: #fff;
  cursor: pointer;
  font-size: 0.85em;
  transition: background 0.25s ease;
`;
toggleBtn.onmouseenter = () => toggleBtn.style.background = "rgba(80,80,80,0.95)";
toggleBtn.onmouseleave = () => toggleBtn.style.background = "rgba(60,60,60,0.9)";

// 🧭 AGORA alterna usando a data inicial (start)
toggleBtn.onclick = () => {
  sortAscending = !sortAscending;
  combined.sort((a, b) => sortAscending ? a.start - b.start : b.start - a.start);
  renderTable(combined, sortSelect.value);
};

controls.appendChild(label);
controls.appendChild(sortSelect);
controls.appendChild(toggleBtn);
root.appendChild(controls);

// -----------------------------
// 🔹 Função de ícone por tipo
function getIconForType(type) {
  if (!type) return "❓";
  const lower = type.toLowerCase();
  if (lower.includes("work")) return "💼";
  if (lower.includes("break")) return "☕";
  if (lower.includes("study")) return "📘";
  if (lower.includes("plan")) return "🗓️";
  return "🎯";
}

// -----------------------------
// 🔹 Renderização da tabela
function renderTable(data, groupBy = "start") {
  const old = root.querySelector("table");
  if (old) old.remove();

  const table = document.createElement("table");
  table.style.cssText = `
    width:100%;
    border-collapse:collapse;
    background:rgba(0,0,0,0.7);
    border-radius:6px;
    overflow:hidden;
  `;

  const headers = ["📅 Data", "⏰ Horário", "⏱️ Duração", "🔗 Nota"];
  const thead = document.createElement("thead");
  const trh = document.createElement("tr");
  for (let h of headers) {
    const th = document.createElement("th");
    th.textContent = h;
    th.style.cssText = `
      text-align:left;
      padding:8px 12px;
      border-bottom:2px solid rgba(255,255,255,0.2);
      color:#fff;
      font-size:0.85em;
      background:rgba(255,255,255,0.1);
    `;
    trh.appendChild(th);
  }
  thead.appendChild(trh);
  table.appendChild(thead);

  const tbody = document.createElement("tbody");

  data.forEach(entry => {
    const tr = document.createElement("tr");
    tr.style.borderBottom = "1px solid rgba(255,255,255,0.05)";

    // 🔗 Data com link interno [[YYYY-MM-DD]]
    const tdDate = document.createElement("td");
    const fileName = moment(entry.start).format("YYYY-MM-DD");
    tdDate.appendChild(dv.el("span", `[[${fileName}]]`));
    tdDate.style.cssText = "padding:6px 12px;color:#ccc;font-size:0.85em;";
    tr.appendChild(tdDate);

    // ⏰ Horário com ícone
    const tdTime = document.createElement("td");
    const icon = getIconForType(entry.type);
    tdTime.textContent = `${icon} ${moment(entry.start).format("HH:mm")} → ${moment(entry.end).format("HH:mm")}`;
    tdTime.style.cssText = "padding:6px 12px;color:#ccc;font-size:0.85em;font-family:monospace;";
    tr.appendChild(tdTime);

    // ⏱️ Duração
    const tdDur = document.createElement("td");
    tdDur.textContent = `${Math.ceil(entry.duration)} min`;
    tdDur.style.cssText = "padding:6px 12px;color:#ccc;font-size:0.85em;";
    tr.appendChild(tdDur);

    // 🔗 Arquivo
    const tdFile = document.createElement("td");
    tdFile.style.cssText = "padding:6px 12px;color:#ccc;font-size:0.85em;";
    if (entry.file) tdFile.appendChild(dv.el("span", entry.file.link));
    else tdFile.textContent = "—";
    tr.appendChild(tdFile);

    tbody.appendChild(tr);
  });

  table.appendChild(tbody);
  root.appendChild(table);
}

// Render inicial
renderTable(combined);

// Atualiza conforme select
sortSelect.addEventListener("change", e => {
  const val = e.target.value;
  let sorted = [...combined];
  if (val === "type") sorted.sort((a, b) => (a.type || "").localeCompare(b.type || ""));
  else if (val === "note") sorted.sort((a, b) => ((a.file?.path) || "").localeCompare((b.file?.path) || ""));
  else sorted.sort((a, b) => a.start - b.start);
  renderTable(sorted, val);
});

```