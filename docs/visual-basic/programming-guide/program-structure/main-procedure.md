---
title: Procedimento principal no Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: 641edd2d0e0dde5f509c8fa77ccf65358fa76a31
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833658"
---
# <a name="main-procedure-in-visual-basic"></a>Procedimento principal no Visual Basic
Todos os aplicativos Visual Basic devem conter um procedimento chamado `Main`. Esse procedimento serve como o início do ponto e controle geral para seu aplicativo. O .NET Framework chama seu `Main` procedimento quando ele tiver carregado seu aplicativo e está pronto para transmitir o controle a ele. A menos que você estiver criando um aplicativo do Windows Forms, você deve escrever o `Main` procedimento para aplicativos que executam suas próprias.  
  
 `Main` contém o código que é executado primeiro. No `Main`, determinar qual formulário está para ser carregado pela primeira vez quando o programa é iniciado, descubra se uma cópia do seu aplicativo já está em execução no sistema, estabelecer um conjunto de variáveis para seu aplicativo ou abrir um banco de dados que o aplicativo requer.  
  
## <a name="requirements-for-the-main-procedure"></a>Requisitos para o procedimento principal  
 Um arquivo que é executado em seu próprio (normalmente com uma extensão .exe) deve conter um `Main` procedimento. Uma biblioteca (por exemplo, com extensão. dll) não é executado em seu próprio e não requer um `Main` procedimento. Os requisitos para os diferentes tipos de projetos que você pode criar são da seguinte maneira:  
  
-   Execute aplicativos de console seus próprios, e você deve fornecer pelo menos um `Main` procedimento. .  
  
-   Aplicativos de formulários do Windows executados suas próprias. No entanto, o compilador do Visual Basic gera automaticamente um `Main` procedimento como um aplicativo e você não precisará escrevê-lo.  
  
-   Bibliotecas de classes não exigem um `Main` procedimento. Isso inclui bibliotecas de controle do Windows e bibliotecas de controle de Web. Aplicativos Web são implantados como bibliotecas de classes.  
  
## <a name="declaring-the-main-procedure"></a>Declarando o procedimento principal  
 Há quatro maneiras de declarar o `Main` procedimento. Pode levar argumentos ou não, e ele pode retornar um valor ou não.  
  
> [!NOTE]
>  Se você declarar `Main` em uma classe, você deve usar o `Shared` palavra-chave. Em um módulo `Main` não precisa ser `Shared`.  
  
-   A maneira mais simples é declarar uma `Sub` procedimento que não usam argumentos ou retornar um valor.  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   `Main` também pode retornar um `Integer` valor, que usa o sistema operacional como o código de saída para o seu programa. Outros programas podem testar esse código, examinando o valor de ERRORLEVEL do Windows. Para retornar um código de saída, você deve declarar `Main` como um `Function` procedimento em vez de um `Sub` procedimento.  
  
    ```  
    Module mainModule  
        Function Main() As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   `Main` também pode tirar uma `String` matriz como um argumento. Cada cadeia de caracteres na matriz contém um dos argumentos de linha de comando usados para invocar o seu programa. Você pode executar ações diferentes dependendo dos seus valores.  
  
    ```  
    Module mainModule  
        Function Main(ByVal cmdArgs() As String) As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   Você pode declarar `Main` para examinar os argumentos de linha de comando, mas não retornar um código de saída, da seguinte maneira.  
  
    ```  
    Module mainModule  
        Sub Main(ByVal cmdArgs() As String)  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [Estrutura de um programa Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [/main](../../../visual-basic/reference/command-line-compiler/main.md)
- [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Tipo de Dados Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Tipo de Dados String](../../../visual-basic/language-reference/data-types/string-data-type.md)
