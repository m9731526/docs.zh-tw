---
title: "Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
WS\-AT 通訊協定服務接收到參與者的「重新執行」訊息，但這些參與者並未回應「準備」。因此，交易已中止。  
  
## 描述  
 如果在參與者仍然在「準備」時收到「重新執行」訊息，則會進行追蹤。這是此狀態的不合法訊息，因此交易即將中止。  
  
## 疑難排解  
 接收這項錯誤可能表示參與者 \(包括下層交易管理員\) 已經從失敗復原，不過不確定交易結果並要求其狀態。  
  
## 請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [使用追蹤來疑難排解應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)