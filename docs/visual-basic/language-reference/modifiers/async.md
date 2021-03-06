---
title: "Async (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
caps.latest.revision: 37
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fa15daee8f3b6ddcc137356896a20cf82e0cc1d0
ms.lasthandoff: 03/13/2017

---
# <a name="async-visual-basic"></a>Async (Visual Basic)
`Async`修飾詞表示方法或[lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)它修改為非同步。 這類方法稱為*非同步方法*。  
  
 非同步方法提供了方便進行可能需要長時間執行之工作的方式，而不需封鎖呼叫端的執行緒。 非同步方法的呼叫端可以繼續執行而不要等候非同步方法完成其工作。  
  
> [!NOTE]
>  `Async` 和 `Await` 關鍵字是在 Visual Studio 2012 中引入。 非同步程式設計的簡介，請參閱[使用 Async 和 Await 進行非同步程式設計](../../../visual-basic/programming-guide/concepts/async/index.md)。  
  
 以下範例將示範非同步方法的結構。 依照慣例，非同步方法的名稱會以 "Async" 結尾。  
  
```vb  
  
Public Async Function ExampleMethodAsync() As Task(Of Integer)  
    ' . . .  
  
    ' At the Await expression, execution in this method is suspended and,  
    ' if AwaitedProcessAsync has not already finished, control returns  
    ' to the caller of ExampleMethodAsync. When the awaited task is   
    ' completed, this method resumes execution.   
    Dim exampleInt As Integer = Await AwaitedProcessAsync()  
  
    ' . . .  
  
    ' The return statement completes the task. Any method that is   
    ' awaiting ExampleMethodAsync can now get the integer result.  
    Return exampleInt  
End Function  
```  
  
 通常，所修飾的方法`Async`關鍵字包含至少一個[Await](../../../visual-basic/language-reference/modifiers/async.md)運算式或陳述式。 方法會以同步方式執行，直到達到第一個 `Await`，此時它會暫止，直到等候的工作完成。 同時，控制權會返回方法的呼叫端。 如果方法未包含 `Await` 運算式或陳述式，則方法就不會暫止，並且會像同步方法一樣執行。 編譯器警告通知您，不包含任何非同步方法`Await`因為這種情況可能表示發生錯誤。 如需詳細資訊，請參閱[編譯器錯誤](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md)。  
  
 `Async` 關鍵字是未保留的關鍵字。 它是修飾方法或 Lambda 運算式時的關鍵字。 在所有其他內容中，它會解譯為識別項。  
  
## <a name="return-types"></a>傳回型別  
 非同步方法是[Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)程序，或[函式](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)或<xref:System.Threading.Tasks.Task><xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601></xref:System.Threading.Tasks.Task>的傳回型別中的程序 此方法不可以宣告任何[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)參數。  
  
 您指定`Task(Of TResult)`的非同步方法的傳回型別如果[傳回](../../../visual-basic/language-reference/statements/return-statement.md)方法的陳述式擁有 TResult 類型的運算元。 如果方法完成時未傳回任何有意義的值，則使用 `Task`。 也就是說，呼叫方法會傳回 `Task`，但是當 `Task` 完成時，任何等候 `Await` 的 `Task` 陳述式都不會產生結果值。  
  
 Async 副程式主要是用來定義需要 `Sub` 程序的事件處理常式。 非同步副程式的呼叫端無法等候它，而且無法攔截方法擲回的例外狀況。  
  
 如需詳細資訊和範例，請參閱[非同步傳回型別](../../../visual-basic/programming-guide/concepts/async/async-return-types.md)。  
  
## <a name="example"></a>範例  
 下列範例將示範非同步事件處理常式、非同步 Lambda 運算式及非同步方法。 如需完整範例，使用這些項目，請參閱[逐步解說︰ 存取 Web 使用 Async 和 Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。 您可以下載的逐步解說程式碼[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkId=255191)。  
  
```vb  
  
' An event handler must be a Sub procedure.  
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
    textBox1.Clear()  
    ' SumPageSizesAsync is a method that returns a Task.  
    Await SumPageSizesAsync()  
    textBox1.Text = vbCrLf & "Control returned to button1_Click."  
End Sub  
  
' The following async lambda expression creates an equivalent anonymous  
' event handler.  
AddHandler button1.Click, Async Sub(sender, e)  
                              textBox1.Clear()  
                              ' SumPageSizesAsync is a method that returns a Task.  
                              Await SumPageSizesAsync()  
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."  
                          End Sub  
  
' The following async method returns a Task(Of T).  
' A typical call awaits the Byte array result:  
'      Dim result As Byte() = Await GetURLContents("http://msdn.com")  
Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
    ' The downloaded resource ends up in the variable named content.  
    Dim content = New MemoryStream()  
  
    ' Initialize an HttpWebRequest for the current URL.  
    Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
    ' Send the request to the Internet resource and wait for  
    ' the response.  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
        ' Get the data stream that is associated with the specified URL.  
        Using responseStream As Stream = response.GetResponseStream()  
            ' Read the bytes in responseStream and copy them to content.    
            ' CopyToAsync returns a Task, not a Task<T>.  
            Await responseStream.CopyToAsync(content)  
        End Using  
    End Using  
  
    ' Return the result as a byte array.  
    Return content.ToArray()  
End Function  
  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute></xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>   
 [Await 運算子](../../../visual-basic/language-reference/operators/await-operator.md)   
 [非同步程式設計使用 Async 和 Await](../../../visual-basic/programming-guide/concepts/async/index.md)   
 [逐步解說：使用 Async 和 Await 存取 Web](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
