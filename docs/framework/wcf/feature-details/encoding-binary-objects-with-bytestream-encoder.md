---
title: "以位元組資料流編碼器將二進位物件編碼 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 以位元組資料流編碼器將二進位物件編碼
使用 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> 設定 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 傳送及接收原始二進位資料。  
  
## 位元組資料流訊息編碼器架構  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 使用的二進位訊息編碼器並沒有能力處理、驗證或識別訊息中的基礎二進位資料。資料封裝會編碼為 XML，傳送、接收及解碼。編碼器處理資料的時間，是在資料傳遞到傳輸之後，且在訊息傳送至訊息佇列之前。在功能上，二進位編碼器會將訊息資料包裝在 `<binary>` 項目中進行傳送，而在訊息接收到之後會移除這些項目。  
  
## 使用位元組資料流訊息編碼器  
 下列範例示範實作位元組資料流訊息編碼器的服務合約。  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 下列範例示範正在叫用的服務。  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 如果使用實作訊息基礎結構 \(例如路由器\) 的服務，處理訊息時並不會檢查、驗證訊息，或是與訊息有其他形式的互動，如以下範例所示。  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## 案例  
 在下列案例中，位元組資料流編碼器很有用。  
  
-   使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，在電腦之間傳輸 JPEG 影像。在此案例中，影像將透過外部來源的傳輸送達，而且所傳送的資料是構成影像的未經處理位元組。服務將會接收二進位資料並顯示影像。  
  
-   從訊息佇列中讀取資訊並加以處理。系統將從訊息佇列管理員讀取訊息，並且在即將處理的訊息佇列通道中向上傳遞。訊息佇列通道將做為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 通道堆疊的佇列管理員。  
  
 如果透過訊息佇列通道傳送訊息，寄件者將無法控制從佇列管理員接收的位元組。如果接收處理序無法讀取未經處理的位元組，接收的訊息格式將會呈現錯誤而且無法處理。系統會假設接收處理序能夠將接收的位元組轉譯回可用的格式。