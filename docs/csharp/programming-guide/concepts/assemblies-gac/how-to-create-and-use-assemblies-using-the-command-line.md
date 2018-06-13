---
title: Como criar e usar assemblies usando a linha de comando (C#)
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: ef872992f17eaaeacf451fa10ef792c47445df80
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319638"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a>Como criar e usar assemblies usando a linha de comando (C#)
Um assembly ou uma DLL (biblioteca de vínculo dinâmico), está vinculada ao seu programa em tempo de execução. Para demonstrar a compilação e uso de uma DLL, considere o seguinte cenário:  
  
-   `MathLibrary.DLL`: o arquivo de biblioteca que contém os métodos a serem chamados em tempo de execução. Neste exemplo, a DLL contém dois métodos, `Add` e `Multiply`.  
  
-   `Add`: o arquivo de origem que contém o método `Add`. Ele retorna a soma de seus parâmetros. A classe `AddClass` que contém o método `Add` é um membro do namespace `UtilityMethods`.  
  
-   `Mult`: o código-fonte que contém o método `Multiply`. Ele retorna o produto de seus parâmetros. A classe `MultiplyClass` que contém o método `Multiply` também é um membro do namespace `UtilityMethods`.  
  
-   `TestCode`: o arquivo que contém o método `Main`. Ele usa os métodos no arquivo DLL para calcular a soma e o produto dos argumentos em tempo de execução.  
  
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
  
## <a name="compiling-the-code"></a>Compilando o código  
 Para criar o arquivo `MathLibrary.DLL`, compile os arquivos `Add` e `Mult` usando a seguinte linha de comando.  
  
```csharp  
csc /target:library /out:MathLibrary.DLL Add.cs Mult.cs  
```  
  
 A opção do compilador [/target:library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) informa ao compilador para gerar uma DLL em vez de um arquivo EXE. A opção do compilador [/out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) seguida por um nome de arquivo é usada para especificar o nome de arquivo da DLL. Caso contrário, o compilador usará o primeiro arquivo (`Add.cs`) como o nome da DLL.  
  
 Para compilar o arquivo executável `TestCode.exe`, use a seguinte linha de comando:  
  
```csharp  
csc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.cs  
```  
  
 A opção do compilador **/out** informa ao compilador para gerar um arquivo EXE e especifica o nome do arquivo de saída (`TestCode.exe`). Essa opção do compilador é opcional. A opção do compilador [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) especifica o arquivo ou os arquivos DLL que esse programa usa. Para obter mais informações, consulte [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Para obter mais informações sobre a compilação na linha de comando, consulte [Compilando na linha de comando com csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../../csharp/programming-guide/index.md)  
 [Assemblies e o Cache de Assembly Global (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [Criando uma classe para conter funções de DLL](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
