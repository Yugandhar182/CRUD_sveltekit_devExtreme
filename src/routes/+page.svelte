<script>
  import { onMount } from "svelte";
 
 export let data;
  const candidateData = data.candidatedata.data;

  // Prepare the grid data for dxDataGrid
  const gridData = candidateData.map(item => ({
  
    firstName: item.firstName,
    surname:item.surname,
    email: item.email,
    phone: item.mobile,
    // Define other properties as needed
  }));

  onMount(() => {
    var dataGrid = new DevExpress.ui.dxDataGrid("#dataGrid", {
      dataSource: gridData,
      columns: [
        { dataField: 'firstName', caption: 'firstName' },
        { dataField: 'surname', caption: 'surname' },
        { dataField: 'email', caption: 'Email' },
        { dataField: 'phone', caption: 'Mobile' },
        // Define other columns as needed
      ],
    

      showBorders: true,
      filterRow: {
      visible: true,
     },
     editing: {
      allowDeleting: true,
      allowAdding: true,
      allowUpdating: true,
      mode: "popup",
      form: {
        labelLocation: "top",
      },
      popup: {
        showTitle: true,
      
      },
      texts: {
        saveRowChanges: "Save",
        cancelRowChanges: "Cancel",
        deleteRow: "Delete",
        confirmDeleteMessage: "Are you sure you want to delete this record?",
      },
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
