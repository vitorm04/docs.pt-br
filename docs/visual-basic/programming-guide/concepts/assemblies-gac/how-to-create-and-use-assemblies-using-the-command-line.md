---
title: 'Como: criar e usar Assemblies usando a linha de comando (Visual Basic)'
ms.date: 03/14/2018
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c02f694da4e03b666fa88ea6db8ddb2db4c9637d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a>Como: criar e usar Assemblies usando a linha de comando (Visual Basic)
Um assembly ou uma DLL (biblioteca de vínculo dinâmico), está vinculada ao seu programa em tempo de execução. Para demonstrar a compilação e uso de uma DLL, considere o seguinte cenário:  
  
-   `MathLibrary.DLL`: o arquivo de biblioteca que contém os métodos a serem chamados em tempo de execução. Neste exemplo, a DLL contém dois métodos, `Add` e `Multiply`.  
  
-   `Add`: o arquivo de origem que contém o método `Add`. Ele retorna a soma de seus parâmetros. A classe `AddClass` que contém o método `Add` é um membro do namespace `UtilityMethods`.  
  
-   `Mult`: o código-fonte que contém o método `Multiply`. Ele retorna o produto de seus parâmetros. A classe `MultiplyClass` que contém o método `Multiply` também é um membro do namespace `UtilityMethods`.  
  
-   `TestCode`: o arquivo que contém o método `Main`. Ele usa os métodos no arquivo DLL para calcular a soma e o produto dos argumentos em tempo de execução.  
  
## <a name="example"></a>Exemplo  
  
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
  
 Esse arquivo contém o algoritmo que usa os métodos DLL `Add` e `Multiply`. Ele começa com a análise dos argumentos `num1` e `num2`, inseridos na linha de comando. Em seguida, ele calcula a soma, usando o método `Add` na classe `AddClass` e o produto, usando o método `Multiply` na classe `MultiplyClass`.  
  
 Observe que o `Imports` instrução no início do arquivo permite que você use os nomes de classe não qualificados para referenciar os métodos DLL em tempo de compilação, da seguinte maneira:  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 Caso contrário, você deve usar nomes totalmente qualificados, da seguinte maneira:  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a>Execução  
 Para executar o programa, digite o nome do arquivo EXE, seguido de dois números, da seguinte maneira:  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Para criar o arquivo `MathLibrary.DLL`, compile os arquivos `Add` e `Mult` usando a seguinte linha de comando.  
  
```console  
vbc -target:library -out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 O [-alvo (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) opção de compilador informa ao compilador para gerar uma DLL em vez de um arquivo EXE. O [-out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) opção de compilador seguida por um nome de arquivo é usada para especificar o nome do arquivo DLL. Caso contrário, o compilador usará o primeiro arquivo (`Add.vb`) como o nome da DLL.  
  
 Para compilar o arquivo executável `TestCode.exe`, use a seguinte linha de comando:  
  
```console  
vbc -out:TestCode.exe -reference:MathLibrary.DLL TestCode.vb  
```  
  
 O **-out** opção de compilador informa ao compilador para gerar um arquivo EXE e especifica o nome do arquivo de saída (`TestCode.exe`). Essa opção do compilador é opcional. O [-referência (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) opção de compilador Especifica o arquivo DLL ou arquivos que usa este programa.  
  
 Para obter mais informações sobre a criação da linha de comando, consulte e [Compilando a partir da linha de comando](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos de Programação](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Assemblies e o cache de assembly global (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Criando uma classe para conter funções de DLL](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
