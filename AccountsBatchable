public class AccountsBatch implements Database.Batchable<Integer> {

    // From anonymous apex
        // We will execute batch.
            // Database.executeBatch(class instance, 100);

    // START method: 
    // We start with getting data. We write SOQL to get all records which we want to process.
    // It returns CHUCK (Group) of data to execute method.
    public Database.QueryLocator start(Database.BatchableContext bc) {
        Database.QueryLocator ql = Database.getQueryLocator([SELECT Id, Name, Description, Active__c FROM Account]);
        return ql;
    }

    // EXECUTE method: (List<sObject>) - is called again and again for each CHUNK of records.
    // Process it by satisfying all business logic.
    public void execute(Database.BatchableContext bc, List<Account> scope) {
        List<Account> toUpdate = new List<Account>();
        for (Account eachAcc : scope) {
            if (eachAcc.Active__c != 'No') {
                eachAcc.Description += '...updated via batch.';
                toUpdate.add(eachAcc);
            }
        }
        // Update description by appending '...updated via batch.';
        update toUpdate;
    }

    // FINISH method:
    // in the end it will called.
    public void finish(Database.BatchableContext bc) {
        System.debug('FINISH. Done.');
    }
}
