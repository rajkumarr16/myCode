# tes
to test repo
({!REQUIRESCRIPT("/lightning/lightning.out.js")})
 
import { LightningElement } from 'lwc';
import { NavigationMixin } from 'lightning/navigation';
 
export default class OpenAction extends NavigationMixin(LightningElement) {
    handleClick() {
        var recordId = '{!Account.Id}'; // get the record id of the current page
        var defaultValues = {
            'AccountId': recordId // set the default value for the Account lookup field
        };
 
        this[NavigationMixin.Navigate]({
            type: 'standard__objectPage',
            attributes: {
                objectApiName: 'Account__c',
                actionName: 'new'
            },
            state: {
                defaultFieldValues: JSON.stringify(defaultValues) // set the default values for the fields
            }
        });
    }
})
