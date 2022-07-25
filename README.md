root@stride:~/nearcore# crontab -l
*/5 * * * * sh /home/root/scripts/ping.sh
root@stride:~/nearcore# cat ping.sh
#!/bin/sh
# Ping call to renew Proposal added to crontab

export NEAR_ENV=shardnet
export LOGS=/home/root/logs
export POOLID=xbeelze
export ACCOUNTID=xbeelze.shardnet.near

echo "---" >> $LOGS/all.log
date >> $LOGS/all.log
near call $POOLID.factory.shardnet.near ping '{}' --accountId xbeelze.shardnet.near --gas=300000000000000 >> $LOGS/all.log
near proposals | grep $POOLID >> $LOGS/all.log
near validators current | grep $POOLID >> $LOGS/all.log
near validators next | grep $POOLID >> $LOGS/all.log
