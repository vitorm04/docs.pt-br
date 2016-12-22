---
title: "Como chamar uma fun&#231;&#227;o do Windows que use tipos n&#227;o assinados (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tipos de dados [Visual Basic], numérico"
  - "tipos de dados [Visual Basic], sem assinatura"
  - "tipos de dados [Visual Basic], usando"
  - "funções [Visual Basic], chamando funções do Windows"
  - "tipo de dados UInteger, usando"
  - "tipo de dados ULong, usando"
  - "tipos de dados não assinados"
  - "tipos não assinados"
  - "tipos não assinados, usando"
  - "tipo de dados UShort, usando"
  - "funções do Windows, Chamando "
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como chamar uma fun&#231;&#227;o do Windows que use tipos n&#227;o assinados (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Se você está consumindo uma classe, um módulo ou uma estrutura que tenha membros de tipos inteiro sem sinal, você pode acessar esses membros com [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
### Para chamar uma função do Windows que leva um tipo não assinado  
  
1.  Use um [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) para informar ao [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] que biblioteca mantém a função, qual é seu nome nessa biblioteca, o que é a sua seqüência de chamada e como converter seqüências de caracteres quando chamá\-lo.  
  
2.  No `Declare` declaração, uso `UInteger`, `ULong`, `UShort`, ou `Byte` conforme apropriado para cada parâmetro com um tipo não assinado.  
  
3.  Consulte a documentação para a função do Windows que você está chamando para localizar os nomes e os valores das constantes que ele usa.  Muitos deles são definidos no arquivo WinUser. H.  
  
4.  Declare constantes necessárias em seu código.  As constantes de Windows muitas são valores não assinados de 32 bits, e você deve declarar essas `As``UInteger`.  
  
5.  Chame a função da forma normal.  O exemplo a seguir chama a função do Windows `MessageBox`, que usa um argumento de inteiro não assinado.  
  
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
    >  O `UInteger`, `ULong`, `UShort`, e `SByte` tipos de dados não são parte do [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), para que o código compatível com CLS não pode consumir um componente que usa\-los.  
  
    > [!IMPORTANT]
    >  Fazendo uma chamada para código não gerenciado, como, por exemplo, a interface de programação de aplicativo \(API\) do Windows expõe seu código para possíveis riscos de segurança.  
  
    > [!IMPORTANT]
    >  Chamar a API do Windows requer a permissão de código não gerenciado, que pode afetar sua execução em situações de confiança parcial.  Para obter mais informações, consulte <xref:System.Security.Permissions.SecurityPermission> e [Code Access Permissions](http://msdn.microsoft.com/pt-br/e5ae402f-6dda-4732-bbe8-77296630f675).  
  
## Consulte também  
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Tipo de dados inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Tipo de dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)   
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Instruções passo a passo: chamando APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)