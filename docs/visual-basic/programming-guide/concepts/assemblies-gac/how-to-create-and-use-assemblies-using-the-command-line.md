---
title: 'Como: criar e usar Assemblies usando a linha de comando (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 72f3e91f9fb88019f937dcd281aa14ab4e887daf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a><span data-ttu-id="f9590-102">Como: criar e usar Assemblies usando a linha de comando (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9590-102">How to: Create and Use Assemblies Using the Command Line (Visual Basic)</span></span>
<span data-ttu-id="f9590-103">Um assembly ou uma DLL (biblioteca de vínculo dinâmico), está vinculada ao seu programa em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f9590-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="f9590-104">Para demonstrar a compilação e uso de uma DLL, considere o seguinte cenário:</span><span class="sxs-lookup"><span data-stu-id="f9590-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
-   <span data-ttu-id="f9590-105">`MathLibrary.DLL`: o arquivo de biblioteca que contém os métodos a serem chamados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f9590-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="f9590-106">Neste exemplo, a DLL contém dois métodos, `Add` e `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="f9590-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
-   <span data-ttu-id="f9590-107">`Add`: o arquivo de origem que contém o método `Add`.</span><span class="sxs-lookup"><span data-stu-id="f9590-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="f9590-108">Ele retorna a soma de seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f9590-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="f9590-109">A classe `AddClass` que contém o método `Add` é um membro do namespace `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="f9590-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="f9590-110">`Mult`: o código-fonte que contém o método `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="f9590-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="f9590-111">Ele retorna o produto de seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f9590-111">It returns the product of its parameters.</span></span> <span data-ttu-id="f9590-112">A classe `MultiplyClass` que contém o método `Multiply` também é um membro do namespace `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="f9590-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="f9590-113">`TestCode`: o arquivo que contém o método `Main`.</span><span class="sxs-lookup"><span data-stu-id="f9590-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="f9590-114">Ele usa os métodos no arquivo DLL para calcular a soma e o produto dos argumentos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f9590-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9590-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f9590-115">Example</span></span>  
  
```vb  
' File: Add.vb   
Namespace UtilityMethods  
    Public Class AddClass  
        Public Shared Function Add(ByVal i As Long, ByVal j As Long) As Long  
            Return i + j  
        End Function  
    End Class  
End Namespace  
```  
  
```vb  
' File: Mult.vb  
Namespace UtilityMethods  
    Public Class MultiplyClass  
        Public Shared Function Multiply(ByVal x As Long, ByVal y As Long) As Long  
            Return x * y  
        End Function  
    End Class  
End Namespace  
```  
  
```vb  
' File: TestCode.vb  
  
Imports UtilityMethods  
  
Module Test  
  
    Sub Main(ByVal args As String())  
  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:")  
  
        If args.Length <> 2 Then  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>")  
            Return  
        End If  
  
        Dim num1 As Long = Long.Parse(args(0))  
        Dim num2 As Long = Long.Parse(args(1))  
  
        Dim sum As Long = AddClass.Add(num1, num2)  
        Dim product As Long = MultiplyClass.Multiply(num1, num2)  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum)  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product)  
  
    End Sub  
  
End Module  
  
' Output (assuming 1234 and 5678 are entered as command-line arguments):  
' Calling methods from MathLibrary.DLL:  
' 1234 + 5678 = 6912  
' 1234 * 5678 = 7006652  
```  
  
 <span data-ttu-id="f9590-116">Esse arquivo contém o algoritmo que usa os métodos DLL `Add` e `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="f9590-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="f9590-117">Ele começa com a análise dos argumentos `num1` e `num2`, inseridos na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="f9590-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="f9590-118">Em seguida, ele calcula a soma, usando o método `Add` na classe `AddClass` e o produto, usando o método `Multiply` na classe `MultiplyClass`.</span><span class="sxs-lookup"><span data-stu-id="f9590-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="f9590-119">Observe que o `Imports` instrução no início do arquivo permite que você use os nomes de classe não qualificados para referenciar os métodos DLL em tempo de compilação, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f9590-119">Notice that the  `Imports` statement at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 <span data-ttu-id="f9590-120">Caso contrário, você deve usar nomes totalmente qualificados, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f9590-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a><span data-ttu-id="f9590-121">Execução</span><span class="sxs-lookup"><span data-stu-id="f9590-121">Execution</span></span>  
 <span data-ttu-id="f9590-122">Para executar o programa, digite o nome do arquivo EXE, seguido de dois números, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f9590-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f9590-123">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="f9590-123">Compiling the Code</span></span>  
 <span data-ttu-id="f9590-124">Para criar o arquivo `MathLibrary.DLL`, compile os arquivos `Add` e `Mult` usando a seguinte linha de comando.</span><span class="sxs-lookup"><span data-stu-id="f9590-124">To build the file `MathLibrary.DLL`, compile the two files `Add` and `Mult` by using the following command line.</span></span>  
  
```vb  
vbc /target:library /out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 <span data-ttu-id="f9590-125">O [/target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) opção de compilador informa ao compilador para gerar uma DLL em vez de um arquivo EXE.</span><span class="sxs-lookup"><span data-stu-id="f9590-125">The [/target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) compiler option tells the compiler to output a DLL instead of an EXE file.</span></span> <span data-ttu-id="f9590-126">O [entrada/saída (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) opção de compilador seguida por um nome de arquivo é usada para especificar o nome do arquivo DLL.</span><span class="sxs-lookup"><span data-stu-id="f9590-126">The [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) compiler option followed by a file name is used to specify the DLL file name.</span></span> <span data-ttu-id="f9590-127">Caso contrário, o compilador usará o primeiro arquivo (`Add.vb`) como o nome da DLL.</span><span class="sxs-lookup"><span data-stu-id="f9590-127">Otherwise, the compiler uses the first file (`Add.vb`) as the name of the DLL.</span></span>  
  
 <span data-ttu-id="f9590-128">Para compilar o arquivo executável `TestCode.exe`, use a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="f9590-128">To build the executable file, `TestCode.exe`, use the following command line:</span></span>  
  
```vb  
vbc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.vb  
```  
  
 <span data-ttu-id="f9590-129">A opção do compilador **/out** informa ao compilador para gerar um arquivo EXE e especifica o nome do arquivo de saída (`TestCode.exe`).</span><span class="sxs-lookup"><span data-stu-id="f9590-129">The **/out** compiler option tells the compiler to output an EXE file and specifies the name of the output file (`TestCode.exe`).</span></span> <span data-ttu-id="f9590-130">Essa opção do compilador é opcional.</span><span class="sxs-lookup"><span data-stu-id="f9590-130">This compiler option is optional.</span></span> <span data-ttu-id="f9590-131">O [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) opção de compilador Especifica o arquivo DLL ou arquivos que usa este programa.</span><span class="sxs-lookup"><span data-stu-id="f9590-131">The [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) compiler option specifies the DLL file or files that this program uses.</span></span>  
  
 <span data-ttu-id="f9590-132">Para obter mais informações sobre a criação da linha de comando, consulte e [Compilando a partir da linha de comando](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="f9590-132">For more information about building from the command line, see  and [Building from the Command Line](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9590-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9590-133">See Also</span></span>  
 [<span data-ttu-id="f9590-134">Conceitos de Programação</span><span class="sxs-lookup"><span data-stu-id="f9590-134">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="f9590-135">Assemblies e o cache de assembly global (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9590-135">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="f9590-136">Criando uma classe para conter funções de DLL</span><span class="sxs-lookup"><span data-stu-id="f9590-136">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
