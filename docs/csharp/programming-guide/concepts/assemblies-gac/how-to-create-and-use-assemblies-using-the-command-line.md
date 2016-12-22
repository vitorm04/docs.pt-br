---
title: "Como: criar e usar Assemblies usando a linha de comando (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: criar e usar Assemblies usando a linha de comando (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um assembly ou uma biblioteca de vínculo dinâmica \(DLL\), está vinculada ao seu programa em tempo de execução. Para demonstrar a criação e uso de uma DLL, considere o seguinte cenário:  
  
-   `MathLibrary.DLL`: O arquivo de biblioteca que contém os métodos sejam chamados em tempo de execução. Neste exemplo, a DLL contém dois métodos, `Add` e `Multiply`.  
  
-   `Add`: O arquivo de origem que contém o método `Add`. Retorna a soma de seus parâmetros. A classe `AddClass` que contém o método `Add` é um membro do namespace `UtilityMethods`.  
  
-   `Mult`: O código\-fonte que contém o método `Multiply`. Retorna o produto de seus parâmetros. A classe `MultiplyClass` que contém o método `Multiply` também é membro do namespace `UtilityMethods`.  
  
-   `TestCode`: O arquivo que contém o `Main` método. Ele usa os métodos no arquivo DLL para calcular a soma e o produto dos argumentos de tempo de execução.  
  
## Exemplo  
  
```c#  
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
  
```c#  
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
  
```c#  
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
  
 Esse arquivo contém o algoritmo que usa os métodos DLL, `Add` e `Multiply`. Ele começa com a análise de argumentos inseridos na linha de comando, `num1` e `num2`. Em seguida, ele calcula a soma usando o `Add` método o `AddClass` classe e o produto usando o `Multiply` método o `MultiplyClass` classe.  
  
 Observe que o `using` diretiva no início do arquivo permite que você use os nomes de classe não qualificados para fazer referência os métodos DLL em tempo de compilação, da seguinte maneira:  
  
```c#  
MultiplyClass.Multiply(num1, num2);  
```  
  
 Caso contrário, você deve usar nomes totalmente qualificados, da seguinte maneira:  
  
```c#  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## Execução  
 Para executar o programa, digite o nome do arquivo executável, seguido por dois números, da seguinte maneira:  
  
 `TestCode 1234 5678`  
  
## Compilando o código  
 Para criar o arquivo `MathLibrary.DLL`, compilar os dois arquivos `Add` e `Mult` usando a seguinte linha de comando.  
  
```c#  
csc /target:library /out:MathLibrary.DLL Add.cs Mult.cs  
```  
  
 O [\/target: Library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) opção de compilador informa o compilador para gerar uma DLL em vez de um arquivo EXE. O [\/out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) opção de compilador seguida por um nome de arquivo é usada para especificar o nome do arquivo DLL. Caso contrário, o compilador usa o primeiro arquivo \(`Add.cs`\) como o nome da DLL.  
  
 Para criar o arquivo executável, `TestCode.exe`, use a seguinte linha de comando:  
  
```c#  
csc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.cs  
```  
  
 O **\/out** opção de compilador informa o compilador para gerar um arquivo EXE e especifica o nome do arquivo de saída \(`TestCode.exe`\). Essa opção de compilador é opcional. O [\/Reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) opção de compilador Especifica o arquivo DLL ou arquivos que esse programa usa. Para obter mais informações, consulte [\/Reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Para obter mais informações sobre a criação da linha de comando, consulte [Command\-line Building With csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
## Consulte também  
 [Guia de Programação em C\#](../../../../csharp/programming-guide/index.md)   
 [Assemblies e o Cache de Assembly Global \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/assemblies-and-the-global-assembly-cache.md)   
 [Criando uma classe para conter funções de DLL](../Topic/Creating%20a%20Class%20to%20Hold%20DLL%20Functions.md)