<script>
    export let name;

    import { icons } from 'feather-icons';

    // Найдем иконку с заданным именем
    const icon = icons[name];
</script>

<span class="feather-icon" style="width: 24px; height: 24px;">
    {@html icon.toSvg()}
</span>