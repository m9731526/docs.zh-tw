---
title: "&lt;netPeerTcpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "netPeerBinding 項目"
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
caps.latest.revision: 20
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 20
---
# &lt;netPeerTcpBinding&gt;
為對等通道特定的 TCP 訊息定義繫結。  
  
## 語法  
  
```  
  
<netPeerBinding>  
    <binding name="string"  
         closeTimeout="TimeSpan"  
         openTimeout="TimeSpan"   
         receiveTimeout="TimeSpan"  
         sendTimeout="TimeSpan"  
         listenIPAddress="String"  
          maxBufferPoolSize="integer"  
         maxReceiveMessageSize="Integer"   
         port="Integer"  
         <security mode="None/Transport/Message/TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## 屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|closeTimeout|<xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。  這個值應該大於或等於 <xref:System.TimeSpan.Zero>。  預設為 00:01:00。|  
|listenIPAddress|字串，指定對等節點接聽 TCP 訊息的 IP 位址。  預設為 `null`。|  
|maxBufferPoolSize|指定此繫結之緩衝區集區大小上限的整數。  預設為 524,288 個位元組 \(512 \* 1024\)。  Windows Communication Foundation \(WCF\) 的許多部分會使用緩衝區。  每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。  有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，  因此可以避免建立及終結緩衝區的負荷。|  
|maxReceivedMessageSize|正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 \(以位元組為單位，包括標頭\)。  超出此限制之訊息的寄件者將會收到 SOAP 錯誤。  收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。  預設值為 65536。|  
|name|包含繫結之組態名稱的字串。  這個值應該是唯一的，因為它會當做繫結的識別使用。  從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。  如需預設組態和無名稱繫結與行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[WCF 服務的簡化組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。|  
|openTimeout|<xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。  這個值應該大於或等於 <xref:System.TimeSpan.Zero>。  預設為 00:01:00。|  
|連接埠|整數，指定這個繫結處理對等通道 TCP 訊息的網路介面連接埠。  這個值必須介於 <xref:System.Net.IPEndPoint.MinPort> 和 <xref:System.Net.IPEndPoint.MaxPort> 之間。  預設值為 0。|  
|receiveTimeout|<xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。  這個值應該大於或等於 <xref:System.TimeSpan.Zero>。  預設為 00:10:00。|  
|sendTimeout|<xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。  這個值應該大於或等於 <xref:System.TimeSpan.Zero>。  預設為 00:01:00。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。  此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。|  
|[\<resolver\>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|指定這個繫結使用的對等解析程式，將對等網狀結構 ID 解析為對等網狀結構內節點的端點 IP 位址。|  
|[\<安全性\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|定義訊息的安全性設定。  此項目的型別為 <xref:System.ServiceModel.Configuration.PeerSecurityElement>。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<繫結\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|這個項目會保存標準和自訂繫結的集合。|  
  
## 備註  
 這個繫結使用透過 TCP 的對等傳輸，藉此支援對等或多方應用程式的建立。  每個對等節點都可以裝載多個以這個繫結類型所定義的對等通道。  
  
## 範例  
 下列範例示範使用 NetPeerTcpBinding 繫結，此繫結會使用對等通道提供多方通訊。  如需使用這個繫結的詳細案例，請參閱[Net Peer TCP](http://msdn.microsoft.com/zh-tw/31f4db66-edb2-40a6-b92a-14098e92acae)。  
  
```  
<configuration>  
<system.ServiceModel>  
<bindings>  
<netPeerBinding>  
    <binding   
         closeTimeout="00:00:10"  
         openTimeout="00:00:20"   
         receiveTimeout="00:00:30"  
         sendTimeout="00:00:40"  
         maxBufferSize="1001"  
         maxConnections="123"   
         maxReceiveMessageSize="1000">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00"  
            enabled="true" />  
        <security mode="TransportWithMessageCredential">  
            <message clientCredentialType="CardSpace" />  
        </security>  
    </binding>  
</netPeerBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.NetPeerTcpBinding>   
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)   
 [Net Peer TCP](http://msdn.microsoft.com/zh-tw/31f4db66-edb2-40a6-b92a-14098e92acae)   
 [對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)