<script>
    import Search from '$lib/Search.svelte';
  
    let selectedOption = '';
    let otherSelectedOption = '';
  
    function handleSelect(event) {
      selectedOption = event.detail; // Get the selected option from the child component
    }
  </script>
  
  <div class="parent-container">
    <div class="header">Complex Header with Fixed Position</div>
    <div class="sidebar">
      <h3>Sidebar Menu</h3>
      <ul>
        <li>Link 1</li>
        <li>Link 2</li>
        <li>Link 3</li>
      </ul>
    </div>
  
    <div class="content">
    <h1>Custom Select Component with Search</h1>
      <h2>Main Content Area</h2>
      <p>
        In this content area, we will test how the Search component behaves in a complex layout. This includes scrolling, fixed elements, and long content.
      </p>
  
      <h3>Custom Select Component with Search</h3>
      <Search on:select={handleSelect} />
  
      <p>Selected option: {selectedOption}</p>
  
      <!-- Long content to test scrolling behavior -->
      <div class="long-content"></div>
    </div>
  </div>
  
  <div class="footer">Fixed Footer Content</div>

  <style>
    /* Simulate a complex layout with various elements, fixed headers, and overflow scenarios */
    .parent-container {
      display: grid;
      grid-template-columns: 200px 1fr;
      grid-template-rows: 50px 1fr;
      height: 100vh;
      gap: 20px;
    }
  
    .header {
      grid-column: 1 / span 2;
      background-color: lightblue;
      padding: 10px;
      text-align: center;
      position: fixed;
      width: 100%;
      top: 0;
      left: 0;
    }
  
    .sidebar {
      grid-row: 2;
      background-color: lightgray;
      padding: 20px;
      height: calc(100vh - 50px);
      overflow-y: auto;
    }
  
    .content {
      grid-row: 2;
      padding: 20px;
      overflow-y: auto;
    }
  
    /* Complex content with varying heights */
    .long-content {
      height: 2000px;
      background: linear-gradient(to bottom, lightgreen, lightcoral);
    }
  
    .footer {
      background-color: #333;
      color: white;
      text-align: center;
      padding: 10px;
      position: fixed;
      width: 100%;
      bottom: 0;
      left: 0;
    }
  </style>
  