<script>
    export let xScale;
    export let yScale;
    export let hoveredDate;
    export let data;
    export let color;

    const getYValue = (date) =>
        data.filter((d) => new Date(d.date) >= date)[0]?.winprob;
</script>

<circle
    cx={xScale(hoveredDate)}
    cy={yScale(getYValue(hoveredDate))}
    r="7.5"
    fill={color}
    stroke="#f0f0f0"
    pointer-events="none"
/>
<text
    x={xScale(hoveredDate)}
    dx="12"
    y={yScale(getYValue(hoveredDate))}
    pointer-events="none"
    fill={color}
    stroke="#f0f0f0"
    stroke-width="5"
    paint-order="stroke"
>
    {Math.round(getYValue(hoveredDate))} %
</text>

<style>
    text {
        font-weight: 600;
    }
</style>
