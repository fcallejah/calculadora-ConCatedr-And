const MAX_TOTAL = 10;

const baremo = {
  investigacion: {
    max: 4.5,
    items: {
      sexenios: { max: 2.5, factor: 0.4 },
      publicaciones: { max: 1.4, factor: 0.08 },
      tesis: { max: 0.6, factor: 0.18 }
    }
  },
  docencia: {
    max: 3,
    items: {
      anosDocencia: { max: 1.4, factor: 0.12 },
      asignaturas: { max: 0.9, factor: 0.08 },
      tutorias: { max: 0.7, factor: 0.1 }
    }
  },
  transferencia: {
    max: 1.5,
    items: {
      proyectos: { max: 0.7, factor: 0.08 },
      innovacion: { max: 0.45, factor: 0.1 },
      participacion: { max: 0.35, factor: 0.1 }
    }
  },
  otros: {
    max: 1,
    items: {
      premios: { max: 0.4, factor: 0.12 },
      cargos: { max: 0.35, factor: 0.1 },
      formacion: { max: 0.25, factor: 0.1 }
    }
  }
};

const form = document.getElementById("calculatorForm");
const totalScoreEl = document.getElementById("totalScore");
const progressBarEl = document.getElementById("progressBar");
const progressLabelEl = document.getElementById("progressLabel");
const insightBox = document.getElementById("insightBox");

const categoryTotals = {
  investigacion: document.getElementById("totalInvestigacion"),
  docencia: document.getElementById("totalDocencia"),
  transferencia: document.getElementById("totalTransferencia"),
  otros: document.getElementById("totalOtros")
};

const resetBtn = document.getElementById("resetBtn");

function clampToMax(value, max) {
  return Math.min(value, max);
}

function getInputValue(id) {
  const element = document.getElementById(id);
  if (!element) return 0;
  const value = Number(element.value || 0);
  return Number.isFinite(value) ? value : 0;
}

function calculateCategory(categoryKey) {
  const section = baremo[categoryKey];
  let total = 0;

  Object.entries(section.items).forEach(([id, config]) => {
    const rawValue = getInputValue(id);
    const computed = rawValue * config.factor;
    total += clampToMax(computed, config.max);
  });

  total = Number(total.toFixed(2));
  categoryTotals[categoryKey].textContent = total.toFixed(2);
  return total;
}

function buildInsight(total) {
  if (total <= 3) {
    return {
      title: "Puntuación baja",
      text: "Tu escenario actual se sitúa aún por debajo de la referencia orientativa. Conviene priorizar la documentación y reforzar los méritos más valorados."
    };
  }

  if (total <= 6) {
    return {
      title: "Puntuación intermedia",
      text: "Estás en una zona competitiva. Con una mejora puntual en investigación o docencia podrías elevar bastante tu posición."
    };
  }

  if (total <= 8) {
    return {
      title: "Puntuación sólida",
      text: "Tu perfil es muy competitivo. La diferencia con la parte alta probablemente depende de reforzar detales de calidad y trayectoria."
    };
  }

  return {
    title: "Puntuación muy alta",
    text: "Tu perfil parece muy bien posicionado. Aun así, conviene verificar con el baremo oficial y la convocatoria concreta para confirmar cada métrica."
  };
}

function render() {
  const investigation = calculateCategory("investigacion");
  const docencia = calculateCategory("docencia");
  const transfer = calculateCategory("transferencia");
  const other = calculateCategory("otros");

  const total = Number((investigation + docencia + transfer + other).toFixed(2));
  const percent = Math.min((total / MAX_TOTAL) * 100, 100);

  totalScoreEl.textContent = total.toFixed(2);
  progressBarEl.style.width = `${percent}%`;
  progressLabelEl.textContent = `${Math.round(percent)}%`;

  const insight = buildInsight(total);
  insightBox.innerHTML = `<h4>${insight.title}</h4><p>${insight.text}</p>`;
}

form.addEventListener("input", render);

resetBtn.addEventListener("click", () => {
  form.reset();
  render();
});

render();
