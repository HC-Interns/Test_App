## Test App for Backup's

### Recomended way to use the back-up function

~~~

function validateCommit (entryName, entry, header, pkg, sources) {

if(validate(entryName, entry, header, pkg, sources)){
  var backup_commit={"sourceAppDNA":App.DNA.Hash,
  "header": {
        "type":entryName,
        "sig":header.Sig,
        "hash":makeHash(entryName,entry),
        "time":header.Time,
        "nextHeader":header.NextHeader,
        "next":entryName+": "+header.Next,
        "entry":header.EntryLink,
      },
  "content":entry,

  }
  bridge(appDNAHash, zomeName, functionName, backup_commit)
  return true;
}
return false;

}

function validate(entryName, entry, header, pkg, sources){
  switch (entryName) {
    case "profile":
      return true;
    default:
      return false;
  }
}

~~~
