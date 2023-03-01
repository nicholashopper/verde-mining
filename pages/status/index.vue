<template>
    <div class="table-container">
      <div class="circles-container">
        <div v-for="(status, description) in descriptionsStatus" 
                :key="description"
                class="circle"
                :style="{ backgroundColor: status }"><td>{{ description}}</td></div>
      </div>
      
      <table>
        <thead>
          <tr>
            <th>Number</th>
            <th>Description</th>
            <th>Is Alive</th>
            <th>Last Alive Time</th>
            <th>First Alive Time</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="port in filteredPorts" :key="port.number" :style="{ backgroundColor: port.isAlive === 'true' ? 'green' : 'red' }">
            <td>{{ port.number }}</td>
            <td>{{ port.description }}</td>
            <td>{{ port.isAlive }}</td>
            <td>{{ formatTime(port.timeLastAlive) }}</td>
            <td>{{ formatTime(port.timeFirstAlive) }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        ports: [],
      };
    },
    computed: {
      filteredPorts() {
        return this.ports.filter(port => port.description.trim() !== '');
      },
      descriptionsStatus() {
        const status = {};
        for (const port of this.filteredPorts) {
          if (port.description in status) {
            if (status[port.description] === 'yellow') {
              continue;
            } else if (status[port.description] === 'green' && port.isAlive === 'false') {
              status[port.description] = 'yellow';
            } else if (status[port.description] === 'red' && port.isAlive === 'true') {
              status[port.description] = 'yellow';
            } else if (port.isAlive === 'false') {
              status[port.description] = 'red';
            }
          } else {
            status[port.description] = port.isAlive === 'true' ? 'green' : 'red';
          }
        }
        return status;
      },
    },
    mounted() {
      this.fetchPorts();
    },
    methods: {
      async fetchPorts() {
        try {
          const response = await fetch('https://rfhpj02mn7.execute-api.us-east-1.amazonaws.com/health-server');
          const data = await response.json();
          this.ports = data.ports;
        } catch (error) {
          console.error(error);
        }
      },
      formatTime(time) {
        if (!time) {
          return "Unknown"
        }
        const now = new Date();
        const diff = now.getTime() - new Date(time).getTime();
        const seconds = Math.floor(diff / 1000);
        const minutes = Math.floor(seconds / 60);
        const hours = Math.floor(minutes / 60);
        const days = Math.floor(hours / 24);
  
        if (days > 0) {
          return `${days} day${days > 1 ? 's' : ''} ago`;
        } else if (hours > 0) {
          return `${hours} hour${hours > 1 ? 's' : ''} ago`;
        } else if (minutes > 0) {
          return `${minutes} minute${minutes > 1 ? 's' : ''} ago`;
        } else {
          return `${seconds} second${seconds === 1 ? '' : 's'} ago`;
        }
      },
    },
  };
  </script>
  
  <style>
  div {
    margin: 10%;
  }
  
  .table-container {
    display: flex;
    justify-content: center;
    flex-direction: column;
  }
  
  table {
    width: 80%;
    margin: auto;
    text-align: center;
  }
  
  th,
  td {
    color: black;
    padding: 10px;
    text-align: center;
  }
  
  th {
    background-color: #ddd;
  }
  
  .circle {
    width: 100px; 
    height: 100px; 
    border-radius: 50%; 
    background-color: #888; 
    display: flex; 
    font-weight: bold;
  }
  </style>