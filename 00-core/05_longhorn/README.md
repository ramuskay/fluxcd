# Best Practices

- Scale up coreDNS to 2 pods
- Reduce MinimalAvailablePercentage	to 10% (default is 25%) due to dedicated disk

Sources : https://longhorn.io/docs/1.10.1/best-practices

# SystemBackup strategy

1. Always

Longhorn will create a backup for all volumes, regardless of their existing backups  
Ensures that every change is safely stored in the backup target.
- Pros: Maximum safety, minimal risk of data loss.
- Cons: Can generate a lot of backup traffic and storage usage.

NB : Seems not working really properly on my use case... Not doing any backup

2. If not present

Longhorn will create a backup for volumes that either lack an existing backup or have an outdated latest backup.  
Useful for system/critical volumes that should only be backed up once, like system snapshots or initial states.
- Pros: Saves storage and reduces backup traffic.
- Cons: Updates to the volume are not backed up automatically, only the first backup is stored.

3. Disabled

Longhorn will not create backups automatically.
Only snapshots exist locally on the nodes; there’s no offsite backup.  
- Pros: Minimal overhead.
- Cons: If the node fails or data is lost locally, the volume cannot be restored.