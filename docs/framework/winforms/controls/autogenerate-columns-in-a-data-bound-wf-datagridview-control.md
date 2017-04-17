---
title: "如何：在資料繫結 Windows Form DataGridView 控制項中自動產生資料行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "資料行 [Windows Form], 自動產生"
  - "資料格, 自動產生資料行"
  - "DataGridView 控制項 [Windows Form], 資料繫結資料行"
ms.assetid: 699f6f9e-6aa5-4811-902b-6a2c57dec7d6
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：在資料繫結 Windows Form DataGridView 控制項中自動產生資料行
下列程式碼範例示範如何在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示繫結資料來源的資料行。  當 <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> 屬性值為 `true` \(預設值\) 時，就會在資料來源資料表中為每一個資料行建立 <xref:System.Windows.Forms.DataGridViewColumn>。  
  
 如果在您設定 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> 屬性時，<xref:System.Windows.Forms.DataGridView> 控制項已經擁有資料行，現有的繫結資料行就會和資料來源中的資料行做比較，且每當有符合項目時會予以保留。  未繫結的資料行一定會保留，  而在資料來源中沒有符合項目的繫結資料行則會移除。  在控制項中沒有符合項目之資料來源的資料行，會產生新的 <xref:System.Windows.Forms.DataGridViewColumn> 物件，這些物件會加入至 <xref:System.Windows.Forms.DataGridView.Columns%2A> 集合的結尾。  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#020](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#020)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#020](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#020)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `customersDataGridView` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   名為 `customersDataSet` 的 <xref:System.Data.DataSet> 物件，具有名為 `Customers` 資料表。  
  
-   <xref:System?displayProperty=fullName>、<xref:System.Windows.Forms?displayProperty=fullName>、<xref:System.Data?displayProperty=fullName> 和 <xref:System.Xml?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=fullName>   
 [在 Windows Form DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [如何：移除 Windows Form DataGridView 控制項中自動產生的資料行](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)