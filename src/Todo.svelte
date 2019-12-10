<script>
  export let todo;
</script>

<style>
  .todo {
    display: flex;
    flex-direction: row;
    align-items: stretch;
    justify-content: space-between;
    background-color: papayawhip;
    border: 1px solid darksalmon;
    border-radius: 4px;
    padding: 0.5rem;
  }

  .todo:not(:last-child) {
    margin-bottom: 0.5rem;
  }

  .label {
    position: relative;
    display: flex;
    align-items: center;
    color: darksalmon;
    flex-grow: 1;
    cursor: pointer;
    padding-left: 2rem;
    user-select: none;
  }

  .label::before,
  .label::after {
    content: "";
    position: absolute;
    left: 0.25rem;
    top: 50%;
    height: 1rem;
    width: 1rem;
    border-radius: 1rem;
  }

  .label::after {
    transform: translateY(-50%);
    background-color: white;
    box-shadow: 0 0 6px rgba(0, 0, 0, 0.15);
    z-index: 1;
  }

  .label::before {
    background-color: transparent;
    transition: background-color 300ms ease;
    z-index: 2;
    transform: scale(0.5) translate(-0%, -100%);
    transform-origin: 50% 50%;
  }

  .label.checked::before {
    background-color: darksalmon;
  }

  .checkbox {
    width: 0;
    height: 0;
    visibility: hidden;
  }

  .title {
    flex-grow: 1;
    font-size: 1.5rem;
    font-weight: bold;
  }

  .delete {
    display: flex;
    align-items: center;
    justify-content: center;
    border: 0;
    margin: 0;
    color: darksalmon;
    background: none;
    font-weight: bold;
    font-size: 1rem;
    padding: 1rem;
    cursor: pointer;
  }

  .delete:hover {
    opacity: 0.5;
    background-color: darksalmon;
    color: papayawhip;
  }
</style>

<div class="todo">
  <label class="label" class:checked={todo.checked}>
    <input id={todo.id} class="checkbox" type="checkbox" on:change />
    <span class="title">{todo.title}</span>
  </label>
  <button class="delete" type="button" on:click>&times;</button>
</div>
