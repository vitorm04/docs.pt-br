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
ms.openlocfilehash: 1c76e3ade0b383727c3241fdaf5ae44b677559c8
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775690"
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="d7b0e-102">Procedimento principal no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d7b0e-102">Main Procedure in Visual Basic</span></span>
<span data-ttu-id="d7b0e-103">Cada aplicativo de Visual Basic deve conter um procedimento chamado `Main`.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="d7b0e-104">Esse procedimento serve como o ponto de partida e o controle geral para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="d7b0e-105">O .NET Framework chama o procedimento `Main` quando ele carregou o aplicativo e está pronto para passar o controle para ele.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="d7b0e-106">A menos que você esteja criando um aplicativo de Windows Forms, você deve escrever o procedimento de `Main` para aplicativos que são executados por conta própria.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>

 <span data-ttu-id="d7b0e-107">`Main` contém o código que é executado primeiro.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="d7b0e-108">No `Main`, você pode determinar qual formulário deve ser carregado primeiro quando o programa for iniciado, descobrir se uma cópia do seu aplicativo já está em execução no sistema, estabelecer um conjunto de variáveis para seu aplicativo ou abrir um banco de dados que o aplicativo requer.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>

## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="d7b0e-109">Requisitos para o procedimento principal</span><span class="sxs-lookup"><span data-stu-id="d7b0e-109">Requirements for the Main Procedure</span></span>
 <span data-ttu-id="d7b0e-110">Um arquivo que é executado por conta própria (normalmente com extensão. exe) deve conter um procedimento `Main`.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="d7b0e-111">Uma biblioteca (por exemplo, com extensão. dll) não é executada por conta própria e não requer um procedimento de `Main`.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="d7b0e-112">Os requisitos para os diferentes tipos de projetos que você pode criar são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="d7b0e-112">The requirements for the different types of projects you can create are as follows:</span></span>

- <span data-ttu-id="d7b0e-113">Os aplicativos de console são executados por conta própria e você deve fornecer pelo menos um procedimento de `Main`.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span>

- <span data-ttu-id="d7b0e-114">Windows Forms aplicativos são executados por conta própria.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-114">Windows Forms applications run on their own.</span></span> <span data-ttu-id="d7b0e-115">No entanto, o compilador de Visual Basic gera automaticamente um procedimento de `Main` nesse aplicativo, e você não precisa escrever um.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-115">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>

- <span data-ttu-id="d7b0e-116">As bibliotecas de classes não exigem um procedimento `Main`.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-116">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="d7b0e-117">Isso inclui bibliotecas de controle do Windows e bibliotecas de controle da Web.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-117">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="d7b0e-118">Os aplicativos Web são implantados como bibliotecas de classes.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-118">Web applications are deployed as class libraries.</span></span>

## <a name="declaring-the-main-procedure"></a><span data-ttu-id="d7b0e-119">Declarando o procedimento principal</span><span class="sxs-lookup"><span data-stu-id="d7b0e-119">Declaring the Main Procedure</span></span>
 <span data-ttu-id="d7b0e-120">Há quatro maneiras de declarar o procedimento de `Main`.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-120">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="d7b0e-121">Ele pode usar argumentos ou não, e pode retornar um valor ou não.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-121">It can take arguments or not, and it can return a value or not.</span></span>

> [!NOTE]
> <span data-ttu-id="d7b0e-122">Se você declarar `Main` em uma classe, deverá usar a palavra-chave `Shared`.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-122">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="d7b0e-123">Em um módulo, `Main` não precisa ser `Shared`.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-123">In a module, `Main` does not need to be `Shared`.</span></span>

- <span data-ttu-id="d7b0e-124">A maneira mais simples é declarar um procedimento de `Sub` que não use argumentos nem retorne um valor.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-124">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- <span data-ttu-id="d7b0e-125">`Main` também pode retornar um valor de `Integer`, que o sistema operacional usa como o código de saída para seu programa.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-125">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="d7b0e-126">Outros programas podem testar esse código examinando o valor ERRORLEVEL do Windows.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-126">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="d7b0e-127">Para retornar um código de saída, você deve declarar `Main` como um procedimento `Function` em vez de um procedimento `Sub`.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-127">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>

    ```vb
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

- <span data-ttu-id="d7b0e-128">`Main` também pode pegar uma matriz `String` como um argumento.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-128">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="d7b0e-129">Cada cadeia de caracteres na matriz contém um dos argumentos de linha de comando usados para invocar seu programa.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-129">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="d7b0e-130">Você pode executar ações diferentes dependendo de seus valores.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-130">You can take different actions depending on their values.</span></span>

    ```vb
    Module mainModule
        Function Main(ByVal cmdArgs() As String) As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
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

- <span data-ttu-id="d7b0e-131">Você pode declarar `Main` para examinar os argumentos de linha de comando, mas não retornar um código de saída, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="d7b0e-131">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>

    ```vb
    Module mainModule
        Sub Main(ByVal cmdArgs() As String)
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```
  
## <a name="see-also"></a><span data-ttu-id="d7b0e-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7b0e-132">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="d7b0e-133">Estrutura de um programa de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d7b0e-133">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="d7b0e-134">-main</span><span class="sxs-lookup"><span data-stu-id="d7b0e-134">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="d7b0e-135">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="d7b0e-135">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="d7b0e-136">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="d7b0e-136">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="d7b0e-137">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="d7b0e-137">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="d7b0e-138">Tipo de Dados Integer</span><span class="sxs-lookup"><span data-stu-id="d7b0e-138">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="d7b0e-139">Tipo de Dados String</span><span class="sxs-lookup"><span data-stu-id="d7b0e-139">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
