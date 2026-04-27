# A Second Cup

This is where I'll post observations and thoughts about programming as I pure my Bachelor's degree in computer science. I obsess over curation and organization wih a passion and have a ntural interest in well-built systems, in general.

### Who I Am
I'm a sous-chef turned programmer after embracing a life-long obsession with the craft. Software should matter. Good software should be maintained and cared. I am a thirty-something Canadian who spent my life working in restaurants and mining camps while reading Kernighan's C Programming Language in my bedroom at night.

### Beyond the Terminal
When I’m not writing code, you’ll likely find me immersed in other forms of world-building:
*   **Reading:** I try to read about 10-20 books per year. My primary obsessions are grimdark fantasy, cyberpunk, and anything horror! Follow me on GoodReads or BookWyrm for my reviews.
*   **Collecting:** I am an avid collector of TTRPGs, obsessing over their well-built systems, beautiful art, and the concepts kept behind their front pages.
*   **Music & Literature:** Music has been one of the most important things in my life since I was a teenager. My favourite genres are hip hop, post-hardcore, and mid-'00s-mid '10s emo.

### Projects
My work focuses on building high-performance, native tools for collectors and power users.

*   **[CalibreQuarry](https://github.com/VirInvictus/CalibreQuarry)** – A Python-based CLI and TUI toolkit for Calibre libraries that reads `metadata.db` directly. It features advanced auditing, catalog generation, and AI-readable exports for large-scale collection management.
*   **[Hermitage](https://github.com/VirInvictus/Hermitage)** – A visually immersive, local-first media sanctuary for Calibre. Built with GTK 4 and Libadwaita, it transforms book browsing into a cinematic gallery experience with high-performance thumbnailing and dynamic color quantization.
*   **[Lattice](https://github.com/VirInvictus/Lattice)** – A comprehensive toolkit for music collectors. It provides ASCII library visualization, parallel integrity verification for various audio formats, and robust metadata auditing via a unified CLI/TUI interface.
*   **[Framework](https://github.com/VirInvictus/Framework)** – A native GNOME document viewer engineered for speed. Utilizing MuPDF and DjVuLibre, it offers a "SumatraPDF-like" high-velocity experience for PDF and DjVu files with a modern libadwaita UI.
*   **[deadbeef-cui](https://github.com/VirInvictus/deadbeef-cui)** – A C GTK plugin for the DeaDBeeF music player, bringing faceted browsing and multi-pane filtering to the Linux desktop, inspired by foobar2000’s Columns UI.
*   **Viaduct** (still under intense development) - A rust-based port of the NetNewsWire RSS reader for MacOS. Built for Gnome/GTK.

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
