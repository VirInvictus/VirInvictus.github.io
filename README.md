# A Second Cup

Welcome to my digital garden. I am a Computer Science student currently pursuing my Bachelor’s degree, driven by a deep-seated obsession with curation, organization, and the elegant systems that power our world.

### Who I Am
My approach to coding is shaped by a commitment to clarity and precision. I believe that software should be as well-structured as a well-loved library. Whether I’m architecting a system or refining a codebase, I strive for an equilibrium between professional rigor and humble curiosity.

### Beyond the Terminal
When I’m not writing code, you’ll likely find me immersed in other forms of world-building:
*   **Reading:** I have a profound love for fantasy novels—I'm drawn to stories that explore complex systems and expansive lore.
*   **Collecting:** I am an avid collector of TTRPGs, valuing the intricate mechanics and collaborative storytelling they offer.
*   **Music & Literature:** These aren't just hobbies; they are obsessions that fuel my creativity and provide a constant rhythm to my work.

### Projects
My work focuses on building high-performance, native tools for collectors and power users.

*   **[CalibreQuarry](https://github.com/VirInvictus/CalibreQuarry)** – A Python-based CLI and TUI toolkit for Calibre libraries that reads `metadata.db` directly. It features advanced auditing, catalog generation, and AI-readable exports for large-scale collection management.
*   **[Hermitage](https://github.com/VirInvictus/Hermitage)** – A visually immersive, local-first media sanctuary for Calibre. Built with GTK 4 and Libadwaita, it transforms book browsing into a cinematic gallery experience with high-performance thumbnailing and dynamic color quantization.
*   **[Lattice](https://github.com/VirInvictus/Lattice)** – A comprehensive toolkit for music collectors. It provides ASCII library visualization, parallel integrity verification for various audio formats, and robust metadata auditing via a unified CLI/TUI interface.
*   **[Framework](https://github.com/VirInvictus/Framework)** – A native GNOME document viewer engineered for speed. Utilizing MuPDF and DjVuLibre, it offers a "SumatraPDF-like" high-velocity experience for PDF and DjVu files with a modern libadwaita UI.
*   **[deadbeef-cui](https://github.com/VirInvictus/deadbeef-cui)** – A C GTK plugin for the DeaDBeeF music player, bringing faceted browsing and multi-pane filtering to the Linux desktop, inspired by foobar2000’s Columns UI.

This space is a collection of my thoughts, code, and the various projects I’m currently cultivating. Thanks for stopping by.

### Recent Blog Posts
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a> 
      <span style="color: #a1a1aa; font-size: 0.9em; margin-left: 10px;">{{ post.date | date: "%Y-%m-%d" }}</span>
    </li>
  {% endfor %}
</ul>
