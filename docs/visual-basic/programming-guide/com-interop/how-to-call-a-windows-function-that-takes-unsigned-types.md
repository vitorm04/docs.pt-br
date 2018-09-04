---
title: Como chamar uma função do Windows que use tipos não assinados (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: d66b74f06abe6b337c24859c444f7a8c2aa52c13
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524559"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>Como chamar uma função do Windows que use tipos não assinados (Visual Basic)
Se você estiver consumindo uma classe, módulo ou estrutura que tem membros de tipos de inteiro sem sinal, você pode acessar esses membros com o Visual Basic.  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>Para chamar uma função do Windows que usa um tipo sem sinal  
  
1.  Use uma [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) para informar ao Visual Basic qual biblioteca contém a função, o que seu nome é nessa biblioteca, o que é a sua sequência de chamada e como converter cadeias de caracteres ao chamá-la.  
  
2.  No `Declare` instrução, use `UInteger`, `ULong`, `UShort`, ou `Byte` conforme apropriado para cada parâmetro com um tipo sem sinal.  
  
3.  Consulte a documentação para a função do Windows chamado para localizar os nomes e valores de constantes que são usadas. Muitos deles são definidos no arquivo WinUser h.  
  
4.  Declare constantes necessárias em seu código. As constantes de Windows muitos são valores sem sinal de 32 bits, e você deve declarar essas `As``UInteger`.  
  
5.  Chame a função da maneira normal. O exemplo a seguir chama a função do Windows `MessageBox`, que leva um argumento de inteiro sem sinal.  
  
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
    >  O `UInteger`, `ULong`, `UShort`, e `SByte` tipos de dados não são parte do [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), então um código compatível com CLS não pode consumir um componente que usa-los.  
  
    > [!IMPORTANT]
    >  Fazer uma chamada para código não gerenciado, como a interface de programação de aplicativo (API) do Windows expõe seu código possíveis riscos de segurança.  
  
    > [!IMPORTANT]
    >  Chamar a API do Windows requer a permissão de código não gerenciado, que pode afetar sua execução em situações de confiança parcial. Para obter mais informações, consulte <xref:System.Security.Permissions.SecurityPermission> e [permissões de acesso do código](https://msdn.microsoft.com/library/e5ae402f-6dda-4732-bbe8-77296630f675).  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)  
 [Tipo de Dados Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Tipo de Dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Instruções passo a passo: chamando APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
