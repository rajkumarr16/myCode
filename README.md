import { LightningElement, track } from 'lwc';
import myIcon from '@salesforce/resourceUrl/myIcon';

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
                type: 'button-icon', 
                fieldName: 'checkbox', 
                label: 'Select', 
                typeAttributes: { 
                    iconName: { fieldName: 'iconName' }, 
                    alternativeText: 'Select Row', 
                    title: 'Select Row',
                    variant: 'bare',
                    name: 'select',
                    disabled: { fieldName: 'disabled' },
                    value: { fieldName: 'id' }
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
