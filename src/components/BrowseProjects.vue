<template>
    <div class="wrapper">
        <side-bar></side-bar>

        <div class="search-projects-bar">
            <div class="projects-text">Browse Projects</div>
            <input class="search" type="text" placeholder="Search on...">
            <select class="select" v-bind="this.selected">
                <option value="0">Title</option>
                <option value="1">Project</option>
                <option value="2">Sector</option>
                <option value="3">User</option>
                <option value="4">Area</option>
            </select>
        </div>
        <projectHolder apiURL="http://localhost:5000/project/all" storageKey="browseProjectsCache" />
    </div>
</template>

<script>
    import axios from 'axios';
    import SideBar from "./Helpercomponents/SideBar";
    import LineChart from './Helpercomponents/LineChart';
    import projectHolder from './Helpercomponents/ProjectHolder';

    export default {
        name: "BrowseProjects",
        components: {SideBar, projectHolder},
        data() {
            return{ selected: this.selected }
        }
    }
</script>

<style scoped>
    .wrapper{
        display: grid;
        grid-template-columns: 16.8vw 80vw;
        grid-template-rows: 15vh 5vh 60vh;
    }

    .search-projects-bar{
        grid-column: 2/3;
        grid-row: 1/2;
        display: grid;
        width: 83.2vw;
        grid-template-rows: 100%;
        grid-template-columns: repeat(5, 1fr);
        align-items: center;
        justify-items: center;
        box-shadow: 0 5px 10px 0 rgba(0, 0, 0, 0.1);
        background-color: #fafafa;
        white-space: nowrap;
    }

    .projects-text{
        font-size: 3em;
        margin-left: 10vw;
        grid-column: 1/2;
    }

    .search{
        margin-left: 5vw;
        grid-column: 2/4;
        width: 100%;
        border-radius: 20px;
        text-indent: 20px;
    }

    .square{
        background-color: black;
        border-radius: 20px;
    }
</style>