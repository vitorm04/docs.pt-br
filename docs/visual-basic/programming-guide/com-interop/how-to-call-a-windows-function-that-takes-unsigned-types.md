---
title: "Como chamar uma função do Windows que use tipos não assinados (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Windows functions [Visual Basic], calling
- unsigned data types [Visual Basic]
- UShort data type [Visual Basic], using
- functions [Visual Basic], calling Windows functions
- ULong data type [Visual Basic], using
- UInteger data type [Visual Basic], using
- data types [Visual Basic], using
- unsigned types [Visual Basic]
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types [Visual Basic], using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3663ca5d3e0e2c94530d4a19ebff0022f495f3d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>Como chamar uma função do Windows que use tipos não assinados (Visual Basic)
Se você está consumindo uma classe, módulo ou estrutura que tem membros de tipos de inteiro sem sinal, você pode acessar esses membros com [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>Para chamar uma função do Windows que usa um tipo não assinado  
  
1.  Use um [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) para informar [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] qual biblioteca contém a função, o que é o nome nessa biblioteca, o que é a sequência de chamada e como converter cadeias de caracteres quando chamá-lo.  
  
2.  No `Declare` instrução, use `UInteger`, `ULong`, `UShort`, ou `Byte` conforme apropriado para cada parâmetro com um tipo não assinado.  
  
3.  Consulte a documentação para a função do Windows que é chamados para localizar os nomes e valores de constantes que são usadas. Muitos desses são definidos no arquivo WinUser.  
  
4.  Declare as constantes necessário em seu código. Muitas constantes do Windows são valores sem sinal de 32 bits, e você deve declarar essas `As``UInteger`.  
  
5.  Chame a função da maneira normal. O exemplo a seguir chama a função do Windows `MessageBox`, que usa um argumento de número inteiro sem sinal.  
  
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
    >  O `UInteger`, `ULong`, `UShort`, e `SByte` tipos de dados não são parte do [independência da linguagem e componentes independentes da linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), então um código compatível com CLS não pode consumir um componente que usa-los.  
  
    > [!IMPORTANT]
    >  Fazer uma chamada para código não gerenciado, como a interface de programação de aplicativo (API) do Windows expõe seu código para possíveis riscos à segurança.  
  
    > [!IMPORTANT]
    >  Chamar a API do Windows requer permissão de código não gerenciado, o que pode afetar sua execução em situações de confiança parcial. Para obter mais informações, consulte <xref:System.Security.Permissions.SecurityPermission> e [permissões de acesso do código](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675).  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tipo de Dados Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Tipo de Dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Instruções passo a passo: chamando APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
