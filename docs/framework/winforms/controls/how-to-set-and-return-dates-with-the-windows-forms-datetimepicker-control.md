---
title: "如何：使用 Windows Form DateTimePicker 控制項設定和傳回日期 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "日期, 在 DateTimePicker 中設定"
  - "DateTimePicker 控制項 [Windows Form], 設定和傳回日期"
  - "範例 [Windows Form], DateTimePicker 控制項"
ms.assetid: a8a48d68-e4b5-426e-9764-51230fc9acd2
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：使用 Windows Form DateTimePicker 控制項設定和傳回日期
在 Windows Form <xref:System.Windows.Forms.DateTimePicker> 控制項中目前選取的日期或時間取決於 <xref:System.Windows.Forms.DateTimePicker.Value%2A> 屬性。  您可以在顯示控制項之前 \(例如，在設計階段或在表單的 <xref:System.Windows.Forms.Form.Load> 事件\) 設定 <xref:System.Windows.Forms.DateTimePicker.Value%2A> 屬性來判斷在控制項中一開始所選取的日期。  根據預設，此控制項的 <xref:System.Windows.Forms.DateTimePicker.Value%2A> 設為目前的日期。  如果您在程式碼中變更控制項的 <xref:System.Windows.Forms.DateTimePicker.Value%2A>，控制項會在表單上自動更新以反映新的設定。  
  
 <xref:System.Windows.Forms.DateTimePicker.Value%2A> 屬性傳回 <xref:System.DateTime> 結構做為其值。  有幾個 <xref:System.DateTime> 結構的屬性會傳回所顯示日期的特定資訊。  這些屬性只可以用來傳回值；請勿使用這些來設定值。  
  
-   對於日期值，<xref:System.DateTime.Month%2A> <xref:System.DateTime.Day%2A>和 <xref:System.DateTime.Year%2A> 屬性會傳回所選取日期之時間單位的整數值。  <xref:System.DateTime.DayOfWeek%2A> 屬性會傳回值，表示所選取的是星期幾 \(可能的值會列在 <xref:System.DayOfWeek> 列舉中\)。  
  
-   對於時間值，<xref:System.DateTime.Hour%2A>、<xref:System.DateTime.Minute%2A>、<xref:System.DateTime.Second%2A> 和 <xref:System.DateTime.Millisecond%2A> 屬性會傳回時間單位的整數值。  若要設定控制項來顯示時間，請參閱[如何：使用 DateTimePicker 控制項顯示時間](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md)。  
  
### 設定控制項的日期和時間值  
  
-   設定 <xref:System.Windows.Forms.DateTimePicker.Value%2A> 屬性為日期或時間值。  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### 傳回日期和時間值  
  
-   呼叫 <xref:System.Windows.Forms.DateTimePicker.Text%2A> 屬性來傳回整個值為控制項中的格式，或呼叫 <xref:System.Windows.Forms.DateTimePicker.Value%2A> 屬性的適當方法，以傳回值的一部分。  使用 <xref:System.Windows.Forms.DateTimePicker.ToString%2A> 將資訊轉換成可以向使用者顯示的字串。  
  
    ```vb  
    MessageBox.Show("The selected value is ", DateTimePicker1.Text)  
    MessageBox.Show("The day of the week is ",   
       DateTimePicker1.Value.DayOfWeek.ToString)  
    MessageBox.Show("Millisecond is: ",   
       DateTimePicker1.Value.Millisecond.ToString)  
  
    ```  
  
    ```csharp  
    MessageBox.Show ("The selected value is " +   
       dateTimePicker1.Text);  
    MessageBox.Show ("The day of the week is " +   
       dateTimePicker1.Value.DayOfWeek.ToString());  
    MessageBox.Show("Millisecond is: " +   
       dateTimePicker1.Value.Millisecond.ToString());  
  
    ```  
  
    ```cpp  
    MessageBox::Show (String::Concat("The selected value is ",  
       dateTimePicker1->Text));  
    MessageBox::Show (String::Concat("The day of the week is ",  
       dateTimePicker1->Value.DayOfWeek.ToString()));  
    MessageBox::Show(String::Concat("Millisecond is: ",  
       dateTimePicker1->Value.Millisecond.ToString()));  
    ```  
  
## 請參閱  
 [DateTimePicker 控制項](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)   
 [如何：使用 Windows Form DateTimePicker 控制項顯示自訂格式的日期](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)