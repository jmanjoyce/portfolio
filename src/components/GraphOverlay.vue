<template>
    <div>
        <svg ref="chart"></svg>
    </div>
</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from "vue";
import * as d3 from "d3";

export default defineComponent({
    name: "GraphOverlay",

    mounted() {
        // Sample data for nodes and edges
        console.log("mounte");
        const nodes_ = [
            { id: "node1", label: "Node 1" },
            { id: "node2", label: "Node 2" },
            { id: "node3", label: "Node 3" },
            { id: "node4", label: "Node 4" },
            { id: "node5", label: "Node 5" },
            { id: "node6", label: "Node 6" },
            { id: "node7", label: "Node 7" },
            { id: "node8", label: "Node 8" },
            { id: "node9", label: "Node 9" },
            { id: "node10", label: "Node 10" },
            { id: "node11", label: "Node 11" },
            { id: "node12", label: "Node 12" },
            { id: "node13", label: "Node 13" },
            { id: "node14", label: "Node 14" },
            { id: "node15", label: "Node 15" },
            { id: "node16", label: "Node 16" },
        ];

        const links_ = [
            { source: "node1", target: "node2" },
            { source: "node1", target: "node5" },
            { source: "node1", target: "node6" },
            { source: "node1", target: "node7" },
            { source: "node1", target: "node8" },
            { source: "node2", target: "node3" },
            { source: "node2", target: "node9" },
            { source: "node2", target: "node10" },
            { source: "node2", target: "node11" },
            { source: "node3", target: "node4" },
            { source: "node3", target: "node12" },
            { source: "node3", target: "node13" },
            { source: "node3", target: "node14" },
            { source: "node4", target: "node5" },
            { source: "node4", target: "node15" },
            { source: "node4", target: "node16" },
            { source: "node5", target: "node6" },
            { source: "node6", target: "node7" },
            { source: "node7", target: "node8" },
            { source: "node8", target: "node9" },
            { source: "node9", target: "node10" },
            { source: "node10", target: "node11" },
            { source: "node11", target: "node12" },
            { source: "node12", target: "node13" },
            { source: "node13", target: "node14" },
            { source: "node14", target: "node15" },
            { source: "node15", target: "node16" },
            { source: "node16", target: "node1" },
            { source: "node6", target: "node12" },
            { source: "node7", target: "node11" },
            { source: "node8", target: "node10" },
            { source: "node9", target: "node15" },
            { source: "node10", target: "node14" },
            { source: "node11", target: "node13" },
            { source: "node12", target: "node16" },
        ];

        const data = { nodes_, links_ };

        const parentElement = ref("chart");

        const width = 800;
        const height = 320;

        // Specify the color scale.
        const color = d3.scaleOrdinal(d3.schemeCategory10);

        // // The force simulation mutates links and nodes, so create a copy
        // // so that re-evaluating this cell produces the same result.
        const links = data.links_.map((d) => ({ ...d }));
        const nodes = data.nodes_.map((d) => ({ ...d }));

        // Create a simulation with several forces.
        const simulation = d3
            .forceSimulation(nodes as any)
            .force(
                "link",
                d3.forceLink(links).id((d: any) => d.id)
            )
            .force("charge", d3.forceManyBody().strength(-200))
            .force("center", d3.forceCenter(width / 2, height / 2))
            .on("tick", ticked);

        // Create the SVG container.
        const svg = d3
            .select(this.$refs.chart as any)
            .attr("width", width)
            .attr("height", height)
            .attr("viewBox", [0, 0, width, height])
            .attr("style", "max-width: 100%; height: auto;")
            .append("g");

        // const data = [
        //     { x: 50, y: 50 },
        //     { x: 100, y: 100 },
        //     { x: 150, y: 50 },
        // ];

        // // Append circles to the <g> element based on data
        // svg.selectAll("circle")
        //     .data(data)
        //     .enter()
        //     .append("circle")
        //     .attr("cx", (d: any) => d.x)
        //     .attr("cy", (d: any) => d.y)
        //     .attr("r", 10)
        //     .attr("fill", "steelblue");

        // Add a line for each link, and a circle for each node.
        const link = svg
            .selectAll("line")
            .data(links)
            .enter()
            .append("line")
            .attr("stroke", "#999")
            .attr("stroke-opacity", 0.6)
            .attr("stroke-width", (d: any) => Math.sqrt(d.value));

        const node = svg
            .selectAll("circle")
            .data(nodes)
            .enter()
            .append("circle")
            .attr("r", 6)
            .attr("fill", (d: any) => "white")
            .call(
                (d3.drag() as any)
                    .on("start", dragstarted)
                    .on("drag", dragged)
                    .on("end", dragended)
            );

        // conmsole.log(svg);

        node.append("title").text((d: any) => d.id);

        // Set the position attributes of links and nodes each time the simulation ticks.
        function ticked() {
            link.attr("x1", (d: any) => d.source.x)
                .attr("y1", (d: any) => d.source.y)
                .attr("x2", (d: any) => d.target.x)
                .attr("y2", (d: any) => d.target.y);

            node.attr("cx", (d: any) => d.x).attr("cy", (d: any) => d.y);
        }

        node.call(
            (d3.drag() as any)
                .on("start", dragstarted)
                .on("drag", dragged)
                .on("end", dragended)
        );

        // Set the position attributes of links and nodes each time the simulation ticks.
        simulation.on("tick", () => {
            link.attr("x1", (d: any) => d.source.x)
                .attr("y1", (d: any) => d.source.y)
                .attr("x2", (d: any) => d.target.x)
                .attr("y2", (d: any) => d.target.y);

            node.attr("cx", (d: any) => d.x).attr("cy", (d: any) => d.y);
        });

        // // Reheat the simulation when drag starts, and fix the subject position.
        function dragstarted(event: any) {
            console.log("drag");
            if (!event.active) simulation.alphaTarget(0.3).restart();
            event.subject.fx = event.subject.x;
            event.subject.fy = event.subject.y;
        }

        // Update the subject (dragged node) position during drag.
        function dragged(event: any) {
            event.subject.fx = event.x;
            event.subject.fy = event.y;
        }

        // Restore the target alpha so the simulation cools after dragging ends.
        // Unfix the subject position now that it’s no longer being dragged.
        function dragended(event: any) {
            if (!event.active) simulation.alphaTarget(0);
            event.subject.fx = null;
            event.subject.fy = null;
        }

        // When this cell is re-run, stop the previous simulation.
        // invalidation.then(() => simulation.stop());
        return svg.node();
    },
});
</script>

<style scoped>
/* .graph-overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 10;
} */
   

</style>
