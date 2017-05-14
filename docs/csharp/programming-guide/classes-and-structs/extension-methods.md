---
title: "擴充方法 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
caps.latest.revision: 35
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b12c4b20f65f8cd2b68a55c5d2548b289a560c3c
ms.lasthandoff: 03/13/2017

---
# <a name="extension-methods-c-programming-guide"></a>擴充方法 (C# 程式設計手冊)
擴充方法可讓您在現有類型中「加入」方法，而不需要建立新的衍生類型、重新編譯，或是修改原始類型。 擴充方法是一種特殊的靜態方法，但是會將它們當成擴充類型上的執行個體方法來呼叫。 對於以 C# 和 Visual Basic 撰寫的用戶端程式碼，呼叫擴充方法或是在類型中實際定義的方法，兩者之間並沒有明顯的差別。  
  
 最常見的擴充方法是 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] 標準查詢運算子，這些運算子會將查詢功能新增至現有的 <xref:System.Collections.IEnumerable?displayProperty=fullName> 和 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> 類型。 若要使用標準查詢運算子，請先使用 `using System.Linq` 指示詞將它們帶入範圍內。 接著，任何實作 <xref:System.Collections.Generic.IEnumerable%601> 的類型都會具有執行個體方法，例如 <xref:System.Linq.Enumerable.GroupBy%2A>、<xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.Average%2A> 等。 當您在 <xref:System.Collections.Generic.IEnumerable%601> 類型執行個體 (例如 <xref:System.Collections.Generic.List%601> 或 <xref:System.Array>) 後面鍵入「點」時，即會在 IntelliSense 陳述式完成功能中看到這些額外的方法。  
  
 下列範例將示範如何在整數陣列上呼叫標準查詢運算子 `OrderBy` 方法。 括號括住的運算式就是 Lambda 運算式。 許多標準查詢運算子會將 Lambda 運算式當成參數，但是擴充方法不會強制這樣做。 如需詳細資訊，請參閱 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)。  
  
 [!code-cs[csProgGuideExtensionMethods#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_1.cs)]  
  
 擴充方法會定義為靜態方法，但透過執行個體方法語法呼叫。 擴充方法的第一個參數會指定方法作業所在的類型，而且參數前面會加上 [this](../../../csharp/language-reference/keywords/this.md) 修飾詞。 您必須使用 `using` 指示詞將命名空間明確匯入至原始程式碼，擴充方法才會進入範圍中。  
  
 下列範例顯示針對 <xref:System.String?displayProperty=fullName> 類別定義的擴充方法。 請注意，擴充方法是定義在非巢狀且非泛型的靜態類別內：  
  
 [!code-cs[csProgGuideExtensionMethods#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_2.cs)]  
  
 使用這個 `using` 指示詞就可以將 `WordCount` 擴充方法帶入範圍中：  
  
```  
using ExtensionMethods;  
```  
  
 而使用下列語法，就可以從應用程式中呼叫它：  
  
```  
string s = "Hello Extension Methods";  
int i = s.WordCount();  
```  
  
 在您的程式碼中，可以利用執行個體方法語法來叫用擴充方法。 不過，編譯器所產生的中繼語言 (IL) 會將您的程式碼轉譯為靜態方法上的呼叫。 因此，實際上並未違反封裝 (Encapsulation) 的準則。 事實上，擴充方法無法存取它們所擴充之類型中的私用變數。  
  
 如需詳細資訊，請參閱[如何：實作和呼叫自訂擴充方法](../../../csharp/programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md)。  
  
 一般而言，您呼叫擴充方法的頻率將遠高於實作自己的方法。 因為擴充方法是使用執行個體方法語法進行呼叫，所以不需要任何特殊知識就可以從用戶端程式碼使用它們。 若要啟用特定類型的擴充方法，只要針對定義這些方法所在的命名空間加入 `using` 指示詞即可。 例如，若要使用標準查詢運算子，請將下面這個 `using` 指示詞加入至程式碼：  
  
```  
using System.Linq;  
```  
  
 (您可能也要加入對 System.Core.dll 的參考)。您將會注意到，標準查詢運算子現在出現在 IntelliSense 中，作為適用於大部分 <xref:System.Collections.Generic.IEnumerable%601> 類型的額外方法。  
  
> [!NOTE]
>  雖然標準查詢運算子未針對 <xref:System.String> 出現在 IntelliSense 中，但是您仍然可以使用它們。  
  
## <a name="binding-extension-methods-at-compile-time"></a>在編譯時期繫結擴充方法  
 您可以使用擴充方法來擴充類別或介面，但無法覆寫它們。 而且永遠不會呼叫擁有與介面或類別方法相同名稱和簽章的擴充方法。 在編譯時期，擴充方法的優先順序一律低於類型本身中定義的執行個體方法。 換句話說，如果類型具有名為 `Process(int i)` 的方法，而您的擴充方法也具有相同的簽章，則編譯器一律會繫結至執行個體方法。 編譯器遇到方法引動過程時，會先在類型的執行個體方法中尋找相符項目。 如果找不到相符項目，則會搜尋任何針對該類型定義的擴充方法，並繫結至找到的第一個擴充方法。 下列範例將示範編譯器如何判斷要繫結的擴充方法或執行個體方法。  
  
## <a name="example"></a>範例  
 下列範例將示範 C# 編譯器遵循的規則，用以判斷要將方法呼叫繫結至類型上的執行個體方法，還是繫結至擴充方法。 靜態類別 `Extensions` 包含針對任何實作 `IMyInterface` 之類型定義的擴充方法。 類別 `A`、`B` 和 `C` 都會實作這個介面。  
  
 因為 `MethodB` 擴充方法的名稱和簽章與這些類別已實作的方法完全相同，所以絕不會呼叫該方法。  
  
 當編譯器找不到具有相符簽章的執行個體方法時，就會繫結至相符的擴充方法 (如果有的話)。  
  
 [!code-cs[csProgGuideExtensionMethods#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_3.cs)]  
  
## <a name="general-guidelines"></a>一般方針  
 一般而言，建議您應謹慎地實作擴充方法，而且只有在必要時才實作。 當用戶端程式碼必須擴充現有的類型時，應該盡可能以建立衍生自現有類型的新類型來達成此目的。 如需詳細資訊，請參閱[繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)。  
  
 使用擴充方法來擴充無法變更其原始程式碼的類型時，會有類型實作的變更導致擴充方法中斷的風險。  
  
 如果您要實作所指定類型的擴充方法，請記住下列幾點：  
  
-   如果擴充方法的簽章與類型中定義的方法相同，則絕不會呼叫擴充方法。  
  
-   擴充方法是帶入命名空間層級的範圍。 例如，如果有多個靜態類別在名為 `Extensions` 的單一命名空間中包含擴充方法，則 `using Extensions;` 指示詞會將這些擴充方法全都帶入範圍中。  
  
 針對實作的類別庫，您不應該使用擴充方法阻止組件的版本號碼遞增。 如果您要在擁有其原始程式碼的程式庫中加入重要功能，則應遵循組件版本控制的標準 .NET Framework 方針。 如需詳細資訊，請參閱[組件版本控制](https://msdn.microsoft.com/library/51ket42z)。  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [平行程式設計範例 (包括許多範例擴充方法)](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)   
 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2) (標準查詢運算子概觀)   
 [Conversion rules for Instance parameters and their impact](http://go.microsoft.com/fwlink/?LinkId=112385) (執行個體參數的轉換規則與其影響)   
 [Extension methods Interoperability between languages](http://go.microsoft.com/fwlink/?LinkId=112386) (語言之間擴充方法的互通性)   
 [Extension methods and Curried Delegates](http://go.microsoft.com/fwlink/?LinkId=112387) (擴充方法和局部調用委派)   
 [Extension method Binding and Error reporting](http://go.microsoft.com/fwlink/?LinkId=112388) (擴充方法繫結和錯誤報告)
