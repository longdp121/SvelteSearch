# Searchable Select Component with Svelte

A customizable and lightweight searchable select component built with Svelte. This component allows users to filter and select options from a dropdown list and provides seamless communication with parent components using Svelte's event dispatching.

## Features

- **Searchable Dropdown**: Users can filter through the list of options by typing in the search box.
- **Event Dispatching**: The selected option is passed to the parent component via custom events, allowing easy integration and data sharing.
- **Dynamic Filtering**: Options are filtered based on the user's input.
- **Lightweight**: The component is written entirely in Svelte, taking advantage of its reactive properties and efficient rendering.
- **Robust UI**: Designed to work within complex layouts without breaking the user interface.

## Usage

### Installation

Clone the repository and navigate to the project folder:

```bash
git clone https://github.com/longdp121/SvelteSearch.git
cd searchable-select-svelte
```

Install the necessary dependencies:

```bash
npm install
```

### How to Use

In your Svelte project, import the `Search` component from the repository and use it within your component or page.

```svelte
<script>
  import Search from './Search.svelte';

  let selectedOption = '';

  function handleSelect(event) {
    selectedOption = event.detail; // Capture selected option from Search component
  }
</script>

<h2>Custom Select Component with Search</h2>
<Search on:select={handleSelect} />

<p>Selected option: {selectedOption}</p>
```

You can also customize the list of options by modifying the data array in the `Search.svelte` file.

```svelte
let data = [
  'Apple',
  'Banana',
  'Cherry',
  // Add your custom options here
];
```

### Features in Detail

- **Search Term Handling**: The component filters the data dynamically based on user input and updates the dropdown options accordingly.
- **Dropdown Behavior**: The dropdown automatically hides when the input loses focus or when an option is selected.
- **Clear Input Handling**: When the user clears the input (e.g., by pressing backspace), the selected option is reset, and an empty string is dispatched to the parent component.

### Example of Parent Layout

The component is designed to work seamlessly within complex layouts. Here's an example of using the component within a parent container with fixed headers, footers, and a scrollable content area:

```svelte
<div class="complex-layout">
  <header>Fixed Header</header>
  <main>
    <Search on:select={handleSelect} />
  </main>
  <footer>Fixed Footer</footer>
</div>
```

## Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/longdp121/SvelteSearch/issues) if you have any questions or suggestions.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.