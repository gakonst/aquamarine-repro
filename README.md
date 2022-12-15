# Aquamarine Bug repro:

1. This graph renders on Mermaid Live, (but does not Render on Github?):

```
 graph TB
   handle(NetworkHandle)
   events(NetworkEvents)
   transactions(Transactions Task)
   ethrequest(ETH Request Task)
   discovery(Discovery Task)
   subgraph NetworkManager
     direction LR
     subgraph Swarm
         direction TB
         B1[(Session Manager)]
         B2[(Connection Lister)]
         B3[(Network State)]
     end
  end
  handle <--> |request response channel| NetworkManager
  NetworkManager --> |Network events| events
  transactions <--> |transactions| NetworkManager
  ethrequest <--> |ETH request handing| NetworkManager
  discovery --> |Discovered peers| NetworkManager
```

Mermaid Live link: https://mermaid.live/edit#pako:eNptUsFuwjAM_RUrpyLBYdsNTTuwIXHYdqC90R28xqIV1O2SFISAf1_SJKxM7SW2n1-e49ezKBpJYi5gq7AtIVvkDAAlstxT8knm2Kjdqs8mPUIHYqMjsuwzjxiFrLEwVcM6yQYJZKh3gW1KRT8daZMssxWsfTxokJUumgOpU_IWowGqu28_ZpD_QMYtqR5zXEW9IryvQ-lGSI-o6lC87w0v9t_iYZOkpLUDwuWTryH-uEleG-aoU2nzv-NpE5cDqUFDN5RYuigcfsPwPJu9wCXsBBTp1i6MoLAw0_4y8tD7CvT8KOjNuYTTdQ9NCWLD0pjAn0eB4JyKFTd2xdsx3s06P1P0jyS0RGpESkxFTarGStr_7-yuyIUpqaZczG0oUe1ykfPV9mFnmvTEhZgb1dFUdK20q32r0Lpb--L1F-vG9J0

2. Doing `cargo doc --open` using aquamarine gives a Syntax Error in Graph, presumably because aquamarine uses an older version?
