---
title: 'Como: criar e usar Assemblies usando a linha de comando (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 363bca806736e5540165ea96e9b4fe60d0968098
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a>Como: criar e usar Assemblies usando a linha de comando (Visual Basic)
Um assembly ou uma biblioteca de vínculo dinâmica (DLL), está vinculada ao seu programa em tempo de execução. Para demonstrar a criação e uso de uma DLL, considere o seguinte cenário:  
  
-   `MathLibrary.DLL`: O arquivo de biblioteca que contém os métodos sejam chamados em tempo de execução. Neste exemplo, a DLL contém dois métodos, `Add` e `Multiply`.  
  
-   `Add`: O arquivo de origem que contém o método `Add`. Retorna a soma de seus parâmetros. A classe `AddClass` que contém o método `Add` é um membro do namespace `UtilityMethods`.  
  
-   `Mult`: O código-fonte que contém o método `Multiply`. Retorna o produto de seus parâmetros. A classe `MultiplyClass` que contém o método `Multiply` também é membro do namespace `UtilityMethods`.  
  
-   `TestCode`: O arquivo que contém o `Main` método. Ele usa os métodos no arquivo DLL para calcular a soma e o produto dos argumentos de tempo de execução.  
  
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
  
 Esse arquivo contém o algoritmo que usa os métodos DLL, `Add` e `Multiply`. Ele começa com a análise de argumentos inseridos na linha de comando, `num1` e `num2`. Em seguida, ele calcula a soma usando o `Add` método o `AddClass` classe e o produto usando o `Multiply` método o `MultiplyClass` classe.  
  
 Observe que o `Imports` instrução no início do arquivo permite que você use os nomes de classe não qualificados para fazer referência os métodos DLL em tempo de compilação, da seguinte maneira:  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 Caso contrário, você deve usar nomes totalmente qualificados, da seguinte maneira:  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a>Execução  
 Para executar o programa, digite o nome do arquivo executável, seguido por dois números, da seguinte maneira:  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Para criar o arquivo `MathLibrary.DLL`, compilar os dois arquivos `Add` e `Mult` usando a seguinte linha de comando.  
  
```vb  
vbc /target:library /out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 O [/target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) opção de compilador informa o compilador para gerar uma DLL em vez de um arquivo EXE. O [entrada/saída (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) opção de compilador seguida por um nome de arquivo é usada para especificar o nome do arquivo DLL. Caso contrário, o compilador usa o primeiro arquivo (`Add.vb`) como o nome da DLL.  
  
 Para criar o arquivo executável, `TestCode.exe`, use a seguinte linha de comando:  
  
```vb  
vbc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.vb  
```  
  
 O **/out** opção de compilador informa o compilador para gerar um arquivo EXE e especifica o nome do arquivo de saída (`TestCode.exe`). Essa opção de compilador é opcional. O [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) opção de compilador Especifica o arquivo DLL ou arquivos que esse programa usa.  
  
 Para obter mais informações sobre a criação da linha de comando, consulte e [Compilando a partir da linha de comando](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos de programação](../../../../visual-basic/programming-guide/concepts/index.md)   
 [Assemblies e o Cache de Assembly Global (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Criando uma classe para conter funções de DLL](http://msdn.microsoft.com/library/e08e4c34-0223-45f7-aa55-a3d8dd979b0f)
