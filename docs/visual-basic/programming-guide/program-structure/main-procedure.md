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
ms.openlocfilehash: 109bf94eb91292cfca700a9e456c8ab53e83d68f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="6dfb4-102">Procedimento principal no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6dfb4-102">Main Procedure in Visual Basic</span></span>
<span data-ttu-id="6dfb4-103">Cada aplicativo do Visual Basic deve conter um procedimento chamado `Main`.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="6dfb4-104">Esse procedimento serve como a partir do ponto e controle geral para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="6dfb4-105">O .NET Framework chama o `Main` procedimento quando ele carregar seu aplicativo e está pronto para passá-lo para controle.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="6dfb4-106">A menos que você estiver criando um aplicativo Windows Forms, você deve escrever o `Main` procedimento para aplicativos que são executados em seus próprios.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>  
  
 <span data-ttu-id="6dfb4-107">`Main` contém o código que é executado primeiro.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="6dfb4-108">Em `Main`, determinar qual formulário é carregado pela primeira vez, quando o programa for iniciado, descubra se uma cópia do seu aplicativo já está em execução no sistema, estabelecer um conjunto de variáveis para o seu aplicativo ou abrir um banco de dados que o aplicativo requer.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>  
  
## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="6dfb4-109">Requisitos para o procedimento principal</span><span class="sxs-lookup"><span data-stu-id="6dfb4-109">Requirements for the Main Procedure</span></span>  
 <span data-ttu-id="6dfb4-110">Um arquivo que é executado em seu próprio (normalmente com extensão .exe) deve conter um `Main` procedimento.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="6dfb4-111">Uma biblioteca (por exemplo, com extensão. dll) não é executado em seu próprio e não requer uma `Main` procedimento.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="6dfb4-112">Os requisitos para os diferentes tipos de projetos que você pode criar são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6dfb4-112">The requirements for the different types of projects you can create are as follows:</span></span>  
  
-   <span data-ttu-id="6dfb4-113">Aplicativos de console executam em seus próprios, e você deve fornecer pelo menos um `Main` procedimento.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span> <span data-ttu-id="6dfb4-114">.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-114">.</span></span>  
  
-   <span data-ttu-id="6dfb4-115">Executar seus próprios aplicativos do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-115">Windows Forms applications run on their own.</span></span> <span data-ttu-id="6dfb4-116">No entanto, o compilador do Visual Basic gera automaticamente um `Main` procedimento como um aplicativo e você não precisa gravar um.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-116">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>  
  
-   <span data-ttu-id="6dfb4-117">Bibliotecas de classes não exigem uma `Main` procedimento.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-117">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="6dfb4-118">Esses incluem bibliotecas de controle do Windows e bibliotecas de controles da Web.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-118">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="6dfb4-119">Aplicativos Web são implantados como bibliotecas de classe.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-119">Web applications are deployed as class libraries.</span></span>  
  
## <a name="declaring-the-main-procedure"></a><span data-ttu-id="6dfb4-120">Declarando o procedimento principal</span><span class="sxs-lookup"><span data-stu-id="6dfb4-120">Declaring the Main Procedure</span></span>  
 <span data-ttu-id="6dfb4-121">Há quatro maneiras para declarar o `Main` procedimento.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-121">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="6dfb4-122">Pode levar argumentos ou não, e pode retornar um valor ou não.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-122">It can take arguments or not, and it can return a value or not.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6dfb4-123">Se você declarar `Main` em uma classe, você deve usar o `Shared` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-123">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="6dfb4-124">Em um módulo, `Main` não precisa ser `Shared`.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-124">In a module, `Main` does not need to be `Shared`.</span></span>  
  
-   <span data-ttu-id="6dfb4-125">É a maneira mais simples para declarar um `Sub` procedimento que não usam argumentos ou retornar um valor.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-125">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   <span data-ttu-id="6dfb4-126">`Main` também pode retornar um `Integer` valor, que o sistema operacional usa como o código de saída para o seu programa.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-126">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="6dfb4-127">Outros programas podem testar esse código, examinando o valor de ERRORLEVEL do Windows.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-127">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="6dfb4-128">Para retornar um código de saída, você deve declarar `Main` como um `Function` procedimento em vez de uma `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-128">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>  
  
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
  
-   <span data-ttu-id="6dfb4-129">`Main` também pode usar um `String` matriz como um argumento.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-129">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="6dfb4-130">Cada cadeia de caracteres na matriz contém um dos argumentos de linha de comando usados para invocar o programa.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-130">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="6dfb4-131">Você pode executar ações diferentes dependendo de seus valores.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-131">You can take different actions depending on their values.</span></span>  
  
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
  
-   <span data-ttu-id="6dfb4-132">Você pode declarar `Main` para examinar os argumentos de linha de comando, mas não retornar um código de saída, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="6dfb4-132">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6dfb4-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6dfb4-133">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
 <xref:System.Array.Length%2A>  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [<span data-ttu-id="6dfb4-134">Estrutura de um programa do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6dfb4-134">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="6dfb4-135">/main</span><span class="sxs-lookup"><span data-stu-id="6dfb4-135">/main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)  
 [<span data-ttu-id="6dfb4-136">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="6dfb4-136">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="6dfb4-137">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="6dfb4-137">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="6dfb4-138">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="6dfb4-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="6dfb4-139">Tipo de Dados Integer</span><span class="sxs-lookup"><span data-stu-id="6dfb4-139">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="6dfb4-140">Tipo de Dados String</span><span class="sxs-lookup"><span data-stu-id="6dfb4-140">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
