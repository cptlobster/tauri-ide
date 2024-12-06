<script lang="ts">
  import { invoke } from "@tauri-apps/api/core";
  import Editor from "$lib/Editor.svelte";

  let name = $state("");
  let greetMsg = $state("");

  async function greet(event: Event) {
    event.preventDefault();
    // Learn more about Tauri commands at https://tauri.app/develop/calling-rust/
    greetMsg = await invoke("greet", { name });
  }
</script>

<header>
  <button>File</button>
  <button>Edit</button>
  <!-- <button>View</button>
  <button>Project</button>
  <button>Terminal</button> -->
  <button>Help</button>
</header>
<main class="container">
  <section class="sidebar" style="display: none;">
    <p>Explorer</p>
  </section>
  <section class="main">
    <Editor />
  </section>
  <section class="lower" style="display: none;">
    <p>Lower Pane</p>
  </section>
</main>
<footer>
  <p><a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ">you know the rules and so do I</a></p>
</footer>

<style>
/* layout containers */
main.container {
  display: grid;
  grid-template-areas:
  'sidebar main'
  'sidebar lower';
  grid-template-columns: min-content 1fr;
  grid-template-rows: 1fr min-content;
  flex: 1 0 100%;
}

header, footer {
  flex: 0 0 1rem;
}

section.sidebar {
  grid-area: sidebar;
  resize: horizontal;
  overflow: auto;

  min-width: 200px;
  max-width: 400px;
}

section.main {
  grid-area: main;
  overflow: auto;
}

section.lower {
  grid-area: lower;
  resize: vertical;
  overflow: auto;

  min-height: 200px;
}

/* styling */
section {
  padding: 0.25rem;
  border: 1px solid var(--border);
  display: flex;
  flex-direction: column;
  align-items: stretch;
  justify-content: stretch;
}

header, footer {
  display: flex;
  flex-direction: row;
}

header button {
  border: none;
  border-radius: 0;
}

footer a:link, footer a:visited {
  color: var(--border);
}
footer a:hover {
  color: var(--text);
}
</style>
