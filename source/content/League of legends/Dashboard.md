---
actual_campeon: Syndra
---
```dataviewjs
const actual = dv.current().actual_campeon;

if (!actual) {
    dv.paragraph("⚠️ Por favor, define la propiedad 'actual_campeon' en el Frontmatter de esta nota.");
} else {
    // Título Principal
    dv.header(1, "🎮 Centro de Mando: " + actual);

    // --- 1. CHECKLIST ESPECÍFICA ---
    const championNote = dv.page(actual);
    
    dv.header(2, "✅ Checklist: " + actual);
    if (championNote) {
        const tasks = championNote.file.tasks.filter(t => !t.completed);
        if (tasks.length > 0) {
            dv.taskList(tasks, false);
        } else {
            dv.paragraph("No hay tareas pendientes para este campeón.");
        }
    } else {
        dv.paragraph("❌ Nota de campeón no encontrada: " + actual);
    }

    // Línea separadora
    dv.el("hr", "");

    // --- 2. CHECKLIST GENERAL ---
    dv.header(2, "🧠 Fundamentos (Platino)");
    const general = dv.page("Informe de mejora");
    
    if (general) {
        const genTasks = general.file.tasks.filter(t => !t.completed);
        if (genTasks.length > 0) {
            dv.taskList(genTasks, false);
        } else {
            dv.paragraph("No hay fundamentos pendientes.");
        }
    } else {
        dv.paragraph("⚠️ Nota 'Checklist General' no encontrada.");
    }

    // Línea separadora
    dv.el("hr", "");

    // --- 3. ENLACE AL INFORME ---
    dv.paragraph("🔗 **Acceso al informe completo:** " + (championNote ? championNote.file.link : "No disponible"));
}

```

