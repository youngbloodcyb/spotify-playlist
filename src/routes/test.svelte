<script>
    import Select from 'svelte-select';

    const complexItems = [
		{value: 'chocolate', label: 'Chocolate', group: 'Sweet'},
        {value: 'pizza', label: 'Pizza', group: 'Savory'},
        {value: 'cake', label: 'Cake', group: 'Sweet'},
        {value: 'chips', label: 'Chips', group: 'Savory'},
        {value: 'ice-cream', label: 'Ice Cream', group: 'Sweet'}
	];
</script>

<div class="flex justify-center items-center h-screen">
    <div class="w-60 font-mono">
        <Select items={complexItems}></Select>
    </div>
</div>