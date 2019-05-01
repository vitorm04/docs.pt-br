---
title: 'Como: Criar e usar Assemblies usando a linha de comando (Visual Basic)'
ms.date: 03/14/2018
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
ms.openlocfilehash: eecd644a7b91492f0a78cf969cfa71ae927609ab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022279"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a><span data-ttu-id="a32ab-102">Como: Criar e usar Assemblies usando a linha de comando (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a32ab-102">How to: Create and Use Assemblies Using the Command Line (Visual Basic)</span></span>
<span data-ttu-id="a32ab-103">Um assembly ou uma DLL (biblioteca de vínculo dinâmico), está vinculada ao seu programa em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a32ab-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="a32ab-104">Para demonstrar a compilação e uso de uma DLL, considere o seguinte cenário:</span><span class="sxs-lookup"><span data-stu-id="a32ab-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
- <span data-ttu-id="a32ab-105">`MathLibrary.DLL`: O arquivo de biblioteca que contém os métodos a serem chamados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a32ab-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="a32ab-106">Neste exemplo, a DLL contém dois métodos, `Add` e `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="a32ab-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
- <span data-ttu-id="a32ab-107">`Add`: O arquivo de origem que contém o método `Add`.</span><span class="sxs-lookup"><span data-stu-id="a32ab-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="a32ab-108">Ele retorna a soma de seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="a32ab-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="a32ab-109">A classe `AddClass` que contém o método `Add` é um membro do namespace `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="a32ab-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
- <span data-ttu-id="a32ab-110">`Mult`: O código-fonte que contém o método `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="a32ab-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="a32ab-111">Ele retorna o produto de seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="a32ab-111">It returns the product of its parameters.</span></span> <span data-ttu-id="a32ab-112">A classe `MultiplyClass` que contém o método `Multiply` também é um membro do namespace `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="a32ab-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
- <span data-ttu-id="a32ab-113">`TestCode`: O arquivo que contém o método `Main`.</span><span class="sxs-lookup"><span data-stu-id="a32ab-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="a32ab-114">Ele usa os métodos no arquivo DLL para calcular a soma e o produto dos argumentos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a32ab-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a32ab-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a32ab-115">Example</span></span>  
  
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
  
 <span data-ttu-id="a32ab-116">Esse arquivo contém o algoritmo que usa os métodos DLL `Add` e `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="a32ab-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="a32ab-117">Ele começa com a análise dos argumentos `num1` e `num2`, inseridos na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="a32ab-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="a32ab-118">Em seguida, ele calcula a soma, usando o método `Add` na classe `AddClass` e o produto, usando o método `Multiply` na classe `MultiplyClass`.</span><span class="sxs-lookup"><span data-stu-id="a32ab-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="a32ab-119">Observe que o `Imports` instrução no início do arquivo permite que você use os nomes de classe não qualificados para fazer referência a métodos de DLL em tempo de compilação, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a32ab-119">Notice that the  `Imports` statement at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 <span data-ttu-id="a32ab-120">Caso contrário, você deve usar nomes totalmente qualificados, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a32ab-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a><span data-ttu-id="a32ab-121">Execução</span><span class="sxs-lookup"><span data-stu-id="a32ab-121">Execution</span></span>  
 <span data-ttu-id="a32ab-122">Para executar o programa, digite o nome do arquivo EXE, seguido de dois números, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a32ab-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a32ab-123">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a32ab-123">Compiling the Code</span></span>  
 <span data-ttu-id="a32ab-124">Para criar o arquivo `MathLibrary.DLL`, compile os arquivos `Add` e `Mult` usando a seguinte linha de comando.</span><span class="sxs-lookup"><span data-stu-id="a32ab-124">To build the file `MathLibrary.DLL`, compile the two files `Add` and `Mult` by using the following command line.</span></span>  
  
```console  
vbc -target:library -out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 <span data-ttu-id="a32ab-125">O [-target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) opção de compilador informa ao compilador para gerar uma DLL em vez de um arquivo EXE.</span><span class="sxs-lookup"><span data-stu-id="a32ab-125">The [-target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) compiler option tells the compiler to output a DLL instead of an EXE file.</span></span> <span data-ttu-id="a32ab-126">O [-out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) opção de compilador seguida por um nome de arquivo é usada para especificar o nome do arquivo DLL.</span><span class="sxs-lookup"><span data-stu-id="a32ab-126">The [-out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) compiler option followed by a file name is used to specify the DLL file name.</span></span> <span data-ttu-id="a32ab-127">Caso contrário, o compilador usará o primeiro arquivo (`Add.vb`) como o nome da DLL.</span><span class="sxs-lookup"><span data-stu-id="a32ab-127">Otherwise, the compiler uses the first file (`Add.vb`) as the name of the DLL.</span></span>  
  
 <span data-ttu-id="a32ab-128">Para compilar o arquivo executável `TestCode.exe`, use a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="a32ab-128">To build the executable file, `TestCode.exe`, use the following command line:</span></span>  
  
```console  
vbc -out:TestCode.exe -reference:MathLibrary.DLL TestCode.vb  
```  
  
 <span data-ttu-id="a32ab-129">O **-out** opção de compilador informa ao compilador para gerar um arquivo EXE e especifica o nome do arquivo de saída (`TestCode.exe`).</span><span class="sxs-lookup"><span data-stu-id="a32ab-129">The **-out** compiler option tells the compiler to output an EXE file and specifies the name of the output file (`TestCode.exe`).</span></span> <span data-ttu-id="a32ab-130">Essa opção do compilador é opcional.</span><span class="sxs-lookup"><span data-stu-id="a32ab-130">This compiler option is optional.</span></span> <span data-ttu-id="a32ab-131">O [-referência (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) opção do compilador Especifica o arquivo DLL ou os arquivos que esse programa usa.</span><span class="sxs-lookup"><span data-stu-id="a32ab-131">The [-reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) compiler option specifies the DLL file or files that this program uses.</span></span>  
  
 <span data-ttu-id="a32ab-132">Para obter mais informações sobre a compilação da linha de comando, consulte e [compilando da linha de comando](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="a32ab-132">For more information about building from the command line, see  and [Building from the Command Line](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a32ab-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a32ab-133">See also</span></span>

- [<span data-ttu-id="a32ab-134">Conceitos de Programação</span><span class="sxs-lookup"><span data-stu-id="a32ab-134">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="a32ab-135">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="a32ab-135">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="a32ab-136">Criando uma classe para conter funções de DLL</span><span class="sxs-lookup"><span data-stu-id="a32ab-136">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
