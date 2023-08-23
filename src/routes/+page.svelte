<script>
    import { onMount } from "svelte";
   
    
 
  
    export let data;
    const candidateData = data.candidatedata.data;
  
    // Prepare the grid data for dxDataGrid
    const gridData = candidateData.map(item => ({
      reference: item.id,
      name: item.firstName,
      email: item.email,
      phone: item.mobile,
      // Define other properties as needed
    }));
  
    onMount(() => {
      var dataGrid = new DevExpress.ui.dxDataGrid("#dataGrid", {
        dataSource: gridData,
        columns: [
          { dataField: 'reference', caption: 'ID' },
          { dataField: 'name', caption: 'Name' },
          { dataField: 'email', caption: 'Email' },
          { dataField: 'phone', caption: 'Mobile' },
          // Define other columns as needed
        ],
      

        showBorders: true,

        filterRow: {

            visible: true,

        },
        
       


paging: {

pageSize: 10,

},

// pagination:true,

pager: {

showPageSizeSelector: true,

allowedPageSizes: [ 10, 20],

showInfo: true,

},
      });
    });
  </script>
  
  <main>
    <div id="dataGrid"></div>
  </main>
  