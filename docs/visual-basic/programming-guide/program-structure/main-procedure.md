---
title: Procedimento principal no Visual Basic | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Main
dev_langs:
- VB
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: c328e45a146255d755fd0f1a2d6fcc5a8e4bf743
ms.lasthandoff: 03/13/2017

---
# <a name="main-procedure-in-visual-basic"></a>Procedimento principal no Visual Basic
Todos os aplicativos Visual Basic devem conter um procedimento chamado `Main`. Esse procedimento serve como o início do ponto e controle geral para seu aplicativo. O .NET Framework chama o `Main` procedimento quando ele tiver carregado seu aplicativo e está pronto para passar o controle para ele. A menos que você estiver criando um aplicativo Windows Forms, você deve escrever o `Main` procedimento para aplicativos que executam suas próprias.  
  
 `Main`contém o código que é executado primeiro. Em `Main`, determinar qual formulário é carregado pela primeira vez, quando o programa for iniciado, descubra se uma cópia do seu aplicativo já está em execução no sistema, estabelecer um conjunto de variáveis para seu aplicativo ou abrir um banco de dados que o aplicativo requer.  
  
## <a name="requirements-for-the-main-procedure"></a>Requisitos para o procedimento principal  
 Um arquivo que é executado em seu próprio (normalmente com extensão .exe) deve conter uma `Main` procedimento. Uma biblioteca (por exemplo, com extensão. dll) não é executado em seu próprio e não requer uma `Main` procedimento. Os requisitos para os diferentes tipos de projetos que você pode criar são da seguinte maneira:  
  
-   Aplicativos de console executam em seus próprios e você deve fornecer pelo menos um `Main` procedimento. .  
  
-   Executar seus próprios aplicativos do Windows Forms. No entanto, o compilador do Visual Basic gera automaticamente uma `Main` procedimento como um aplicativo e você não precisa escrever um.  
  
-   Bibliotecas de classes não exigem uma `Main` procedimento. Esses incluem bibliotecas de controle do Windows e bibliotecas de controle da Web. Aplicativos da Web são implantados como bibliotecas de classes.  
  
## <a name="declaring-the-main-procedure"></a>Declarando o procedimento principal  
 Há quatro maneiras de declarar o `Main` procedimento. Pode levar argumentos ou não, e pode retornar um valor ou não.  
  
> [!NOTE]
>  Se você declarar `Main` em uma classe, você deve usar o `Shared` palavra-chave. Em um módulo, `Main` não precisa ser `Shared`.  
  
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
  
-   `Main`também pode retornar um `Integer` valor, que o sistema operacional usa como o código de saída para o seu programa. Outros programas podem testar esse código, examinando o valor de ERRORLEVEL do Windows. Para retornar um código de saída, você deve declarar `Main` como uma `Function` procedimento em vez de uma `Sub` procedimento.  
  
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
  
-   `Main`também pode usar um `String` matriz como um argumento. Cada cadeia de caracteres na matriz contém um dos argumentos de linha de comando usados para chamar o programa. Você pode executar ações diferentes dependendo de seus valores.  
  
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
  
-   Você pode declarar `Main` para examinar os argumentos de linha de comando, mas não retornam um código de saída, da seguinte maneira.  
  
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
 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A></xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>   
 <xref:System.Array.Length%2A></xref:System.Array.Length%2A>   
 <xref:Microsoft.VisualBasic.Information.UBound%2A></xref:Microsoft.VisualBasic.Information.UBound%2A>   
 [Estrutura de um programa Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)   
 [NIB: versão do Visual Basic do Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c)   
 [/Main](../../../visual-basic/reference/command-line-compiler/main.md)   
 [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Instrução sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Tipo de dados inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Tipo de Dados String](../../../visual-basic/language-reference/data-types/string-data-type.md)
