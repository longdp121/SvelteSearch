<script>
    import { createEventDispatcher, onMount } from 'svelte';
  
    const dispatch = createEventDispatcher(); // Event dispatcher
  
    let data = [
      'Apple',
      'Banana',
      'Cherry',
      'Date',
      'Elderberry',
      'Fig',
      'Grapefruit',
      'Honeydew',
      'Kiwi',
      'Lemon',
      'Mango',
      'Nectarine',
      'Orange',
      'Papaya',
      'Quince',
      'Raspberry',
      'Strawberry',
      'Tomato',
      'Ugli fruit',
      'Watermelon'
    ];
  
    let searchTerm = '';
    let showOptions = false;
    let filteredData = [...data];
    let selectedOption = '';
  
    // Filter data when search term changes
    $: filteredData = data.filter(item => item.toLowerCase().includes(searchTerm.toLowerCase()));
  
    // Function to handle selecting an option
    function selectOption(option) {
      selectedOption = option;
      searchTerm = option;
      showOptions = false;
      dispatch('select', option); // Dispatch event when an option is selected
    }
  
    // Function to handle input changes
    function handleInput() {
      if (searchTerm === '') {
        selectedOption = '';
        dispatch('select', ''); // Dispatch empty string when input is cleared
      }
    }
  
    // Close dropdown if clicking outside
    function handleOutsideClick(event) {
      if (!event.target.closest('.select-container')) {
        showOptions = false;
      }
    }
  
    // Mount the event listener for click outside
    onMount(() => {
      document.addEventListener('click', handleOutsideClick);
      return () => document.removeEventListener('click', handleOutsideClick);
    });
  </script>
  
  <div class="select-container">
    <input
      type="text"
      placeholder="Select an option..."
      bind:value={searchTerm}
      on:focus={() => showOptions = true}
      on:input={handleInput}
      autocomplete="off"
    />
    <ul class="{showOptions ? 'show' : ''}">
      {#each filteredData as item}
        <li on:click={() => selectOption(item)}>{item}</li>
      {/each}
    </ul>
  </div>
  
  <style>
    .select-container {
      position: relative;
      display: inline-block;
      width: 200px;
    }
  
    input {
      width: 100%;
      box-sizing: border-box;
      padding: 8px;
    }
  
    ul {
      position: absolute;
      top: 100%;
      left: 0;
      width: 100%;
      box-sizing: border-box;
      border: 1px solid #ccc;
      border-top: none;
      background-color: white;
      max-height: 150px;
      overflow-y: auto;
      margin: 0;
      padding: 0;
      list-style-type: none;
      z-index: 1000;
      display: none;
    }
  
    ul.show {
      display: block;
    }
  
    li {
      padding: 8px;
      cursor: pointer;
    }
  
    li:hover {
      background-color: #f0f0f0;
    }
  </style>
  