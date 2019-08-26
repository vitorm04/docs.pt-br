---
title: 'Como: Criar e usar assemblies usando a linha de comando (C#)'
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: 0a8db22a05d834d15f6e6b7f049f59f86bc1fe1d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595973"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a><span data-ttu-id="abcaa-102">Como: Criar e usar assemblies usando a linha de comando (C#)</span><span class="sxs-lookup"><span data-stu-id="abcaa-102">How to: Create and Use Assemblies Using the Command Line (C#)</span></span>
<span data-ttu-id="abcaa-103">Um assembly ou uma DLL (biblioteca de vínculo dinâmico), está vinculada ao seu programa em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="abcaa-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="abcaa-104">Para demonstrar a compilação e uso de uma DLL, considere o seguinte cenário:</span><span class="sxs-lookup"><span data-stu-id="abcaa-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
- <span data-ttu-id="abcaa-105">`MathLibrary.DLL`: O arquivo de biblioteca que contém os métodos a serem chamados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="abcaa-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="abcaa-106">Neste exemplo, a DLL contém dois métodos, `Add` e `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="abcaa-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
- <span data-ttu-id="abcaa-107">`Add`: O arquivo de origem que contém o método `Add`.</span><span class="sxs-lookup"><span data-stu-id="abcaa-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="abcaa-108">Ele retorna a soma de seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="abcaa-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="abcaa-109">A classe `AddClass` que contém o método `Add` é um membro do namespace `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="abcaa-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
- <span data-ttu-id="abcaa-110">`Mult`: O código-fonte que contém o método `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="abcaa-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="abcaa-111">Ele retorna o produto de seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="abcaa-111">It returns the product of its parameters.</span></span> <span data-ttu-id="abcaa-112">A classe `MultiplyClass` que contém o método `Multiply` também é um membro do namespace `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="abcaa-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
- <span data-ttu-id="abcaa-113">`TestCode`: O arquivo que contém o método `Main`.</span><span class="sxs-lookup"><span data-stu-id="abcaa-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="abcaa-114">Ele usa os métodos no arquivo DLL para calcular a soma e o produto dos argumentos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="abcaa-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abcaa-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="abcaa-115">Example</span></span>  
  
```csharp  
// File: Add.cs   
namespace UtilityMethods  
{  
    public class AddClass   
    {  
        public static long Add(long i, long j)   
        {   
            return (i + j);  
        }  
    }  
}  
```  
  
```csharp  
// File: Mult.cs  
namespace UtilityMethods   
{  
    public class MultiplyClass  
    {  
        public static long Multiply(long x, long y)   
        {  
            return (x * y);   
        }  
    }  
}  
```  
  
```csharp  
// File: TestCode.cs  
  
using UtilityMethods;  
  
class TestCode  
{  
    static void Main(string[] args)   
    {  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:");  
  
        if (args.Length != 2)  
        {  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>");  
            return;  
        }  
  
        long num1 = long.Parse(args[0]);  
        long num2 = long.Parse(args[1]);  
  
        long sum = AddClass.Add(num1, num2);  
        long product = MultiplyClass.Multiply(num1, num2);  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum);  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product);  
    }  
}  
/* Output (assuming 1234 and 5678 are entered as command-line arguments):  
    Calling methods from MathLibrary.DLL:  
    1234 + 5678 = 6912  
    1234 * 5678 = 7006652          
*/  
```  
  
 <span data-ttu-id="abcaa-116">Esse arquivo contém o algoritmo que usa os métodos DLL `Add` e `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="abcaa-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="abcaa-117">Ele começa com a análise dos argumentos `num1` e `num2`, inseridos na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="abcaa-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="abcaa-118">Em seguida, ele calcula a soma, usando o método `Add` na classe `AddClass` e o produto, usando o método `Multiply` na classe `MultiplyClass`.</span><span class="sxs-lookup"><span data-stu-id="abcaa-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="abcaa-119">Observe que a diretiva `using` no início do arquivo permite que você use os nomes de classe não qualificados para fazer referência aos métodos de DLL em tempo de compilação, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="abcaa-119">Notice that the `using` directive at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 <span data-ttu-id="abcaa-120">Caso contrário, você deve usar nomes totalmente qualificados, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="abcaa-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a><span data-ttu-id="abcaa-121">Execução</span><span class="sxs-lookup"><span data-stu-id="abcaa-121">Execution</span></span>  
 <span data-ttu-id="abcaa-122">Para executar o programa, digite o nome do arquivo EXE, seguido de dois números, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="abcaa-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="see-also"></a><span data-ttu-id="abcaa-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="abcaa-123">See also</span></span>

- [<span data-ttu-id="abcaa-124">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="abcaa-124">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="abcaa-125">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="abcaa-125">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="abcaa-126">Criando uma classe para conter funções de DLL</span><span class="sxs-lookup"><span data-stu-id="abcaa-126">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
