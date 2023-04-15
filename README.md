# myCode
to test repo
import { LightningElement, track } from 'lwc';

export default class MyDatatable extends LightningElement {
    @track data = [
        // Add your data here
    ];
    
    columns = [
        // Add your columns here
    ];
    
    get customColumns() {
        return [
            { 
                type: 'checkbox', 
                fieldName: 'checkbox', 
                label: 'Select', 
                typeAttributes: { 
                    rowKeyValue: { fieldName: 'id' } 
                } 
            },
            ...this.columns,
        ];
    }
    
    handleRowSelection(event) {
        const selectedRows = event.detail.selectedRows;
        console.log('Selected Rows: ', selectedRows);
    }
}
