---
title: 'Como: Criar e usar assemblies usando a linha de comando (C#)'
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: 12d23816b740816bd357c3c2ac57583f31bf3cb3
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586026"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a>Como: Criar e usar assemblies usando a linha de comando (C#)
Um assembly ou uma DLL (biblioteca de vínculo dinâmico), está vinculada ao seu programa em tempo de execução. Para demonstrar a compilação e uso de uma DLL, considere o seguinte cenário:  
  
- `MathLibrary.DLL`: O arquivo de biblioteca que contém os métodos a serem chamados em tempo de execução. Neste exemplo, a DLL contém dois métodos, `Add` e `Multiply`.  
  
- `Add`: O arquivo de origem que contém o método `Add`. Ele retorna a soma de seus parâmetros. A classe `AddClass` que contém o método `Add` é um membro do namespace `UtilityMethods`.  
  
- `Mult`: O código-fonte que contém o método `Multiply`. Ele retorna o produto de seus parâmetros. A classe `MultiplyClass` que contém o método `Multiply` também é um membro do namespace `UtilityMethods`.  
  
- `TestCode`: O arquivo que contém o método `Main`. Ele usa os métodos no arquivo DLL para calcular a soma e o produto dos argumentos em tempo de execução.  
  
## <a name="example"></a>Exemplo  
  
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
  
 Esse arquivo contém o algoritmo que usa os métodos DLL `Add` e `Multiply`. Ele começa com a análise dos argumentos `num1` e `num2`, inseridos na linha de comando. Em seguida, ele calcula a soma, usando o método `Add` na classe `AddClass` e o produto, usando o método `Multiply` na classe `MultiplyClass`.  
  
 Observe que a diretiva `using` no início do arquivo permite que você use os nomes de classe não qualificados para fazer referência aos métodos de DLL em tempo de compilação, da seguinte maneira:  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 Caso contrário, você deve usar nomes totalmente qualificados, da seguinte maneira:  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a>Execução  
 Para executar o programa, digite o nome do arquivo EXE, seguido de dois números, da seguinte maneira:  
  
 `TestCode 1234 5678`  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../../csharp/programming-guide/index.md)
- [Assemblies no .NET](../../../../standard/assembly/index.md)
- [Criando uma classe para conter funções de DLL](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
