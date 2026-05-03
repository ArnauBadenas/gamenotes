<%*
const championName = tp.file.title.replace("_Stats", "");

try {
    // Step 1: fetch latest DDragon version dynamically
    const versionRes = await fetch("https://ddragon.leagueoflegends.com/api/versions.json");
    const versions = await versionRes.json();
    const latestVersion = versions[0];

    // Step 2: fetch champion data
    const url = `https://ddragon.leagueoflegends.com/cdn/${latestVersion}/data/en_US/champion/${championName}.json`;
    const response = await fetch(url);
    if (!response.ok) throw new Error(`HTTP ${response.status}`);
    const data = await response.json();
    const stats = data.data[championName];

    tR += `*Versión DDragon: ${latestVersion}*\n\n`;
    tR += `### Habilidades\n\n`;

    // Passive
    const passive = stats.passive;
    const passiveDesc = passive.description.replace(/<[^>]*>/g, "");
    tR += `**${passive.name} (Pasiva)**: ${passiveDesc}\n\n`;

    // Q W E R
    const keys = ["Q", "W", "E", "R"];
    stats.spells.forEach((spell, i) => {
        const desc = spell.description.replace(/<[^>]*>/g, "");
        tR += `**${spell.name} (${keys[i]})**: ${desc}\n`;
        tR += `*CD:* ${spell.cooldownBurn}s | *Coste:* ${spell.costBurn}\n\n`;
    });

} catch (e) {
    tR += `❌ Error: ${e.message}\n`;
    tR += `Revisa que el nombre del archivo sea exactamente el ID interno del campeón (ej: \`Syndra_Stats\`, \`MissFortune_Stats\`).`;
}
%>