---
title: "Como: chamar uma função do Windows que obtém tipos sem-sinal (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Windows functions, calling
- unsigned data types
- UShort data type, using
- functions [Visual Basic], calling Windows functions
- ULong data type, using
- UInteger data type, using
- data types [Visual Basic], using
- unsigned types
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types, using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
caps.latest.revision: 18
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
ms.openlocfilehash: fbff07f4923b0633a2bc9b4fd558d9d51f64370a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>Como chamar uma função do Windows que use tipos não assinados (Visual Basic)
Se você está consumindo uma classe, módulo ou estrutura que possui membros dos tipos inteiros sem sinal, você pode acessar esses membros com [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>Para chamar uma função do Windows que usa um tipo sem sinal  
  
1.  Use um [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) para informar [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] qual biblioteca contém a função, o que é o nome nessa biblioteca, o que é a sequência de chamada e como converter cadeias de caracteres para chamá-lo.  
  
2.  No `Declare` instrução, use `UInteger`, `ULong`, `UShort`, ou `Byte` conforme apropriado para cada parâmetro com um tipo sem sinal.  
  
3.  Consulte a documentação para a função do Windows que você está chamando para localizar os nomes e valores de constantes que são usadas. Muitas delas são definidas no arquivo WinUser. H.  
  
4.  Declare as constantes necessárias em seu código. Muitas constantes do Windows são valores de 32 bits sem sinal, e você deve declarar essas `As``UInteger`.  
  
5.  Chame a função da maneira normal. O exemplo a seguir chama a função do Windows `MessageBox`, que usa um argumento de inteiro não assinado.  
  
    ```  
    Public Class windowsMessage  
        Private Declare Auto Function mb Lib "user32.dll" Alias "MessageBox" (  
            ByVal hWnd As Integer,   
            ByVal lpText As String,   
            ByVal lpCaption As String,   
            ByVal uType As UInteger) As Integer  
        Private Const MB_OK As UInteger = 0  
        Private Const MB_ICONEXCLAMATION As UInteger = &H30  
        Private Const IDOK As UInteger = 1  
        Private Const IDCLOSE As UInteger = 8  
        Private Const c As UInteger = MB_OK Or MB_ICONEXCLAMATION  
        Public Function messageThroughWindows() As String  
            Dim r As Integer = mb(0, "Click OK if you see this!",   
                "Windows API call", c)  
            Dim s As String = "Windows API MessageBox returned " &  
                 CStr(r)& vbCrLf & "(IDOK = " & CStr(IDOK) &  
                 ", IDCLOSE = " & CStr(IDCLOSE) & ")"  
            Return s  
        End Function  
    End Class  
    ```  
  
     Você pode testar a função `messageThroughWindows` com o código a seguir.  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  O `UInteger`, `ULong`, `UShort`, e `SByte` tipos de dados não são parte do [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), então um código compatível com CLS não pode consumir um componente que os utiliza.  
  
    > [!IMPORTANT]
    >  Fazer uma chamada para código não gerenciado, como a interface de programação de aplicativo (API) do Windows expõe seu código possíveis riscos de segurança.  
  
    > [!IMPORTANT]
    >  Chamar a API do Windows requer permissão de código não gerenciado, que pode afetar sua execução em situações de confiança parcial. Para obter mais informações, consulte <xref:System.Security.Permissions.SecurityPermission>e [permissões de acesso de código](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675).</xref:System.Security.Permissions.SecurityPermission>  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Tipo de dados inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Tipo de dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)   
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Instruções passo a passo: chamando APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
