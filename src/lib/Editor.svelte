<script lang="ts">

</script>
<header>
    <input type="text" name="file" />
    <button>Open</button>
    <button>Save</button>
</header>
<textarea></textarea>
<style type="text/css">
textarea {
    resize: none;
    overflow: auto;

    color: var(--text);
    background-color: var(--background);
    height: 100%;
    border: 1px solid var(--border);
    border-radius: 0.25rem;
}

textarea:focus {
    outline: none;
}

header {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
}

input[type="text"] {
    background-color: transparent;
    border: 1px solid var(--background);
    color: var(--text);
}

input[type="text"]:hover, input[type="text"]:focus {
    border: 1px solid var(--border);
}

input[type="text"]:focus {
    outline: none;
}
</style>