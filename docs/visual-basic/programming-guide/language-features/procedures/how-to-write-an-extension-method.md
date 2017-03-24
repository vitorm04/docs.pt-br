---
title: "Como: gravar um método de extensão (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- extending data types
- writing extension methods
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7624b9934ba23699221019eb4ab8632bd967f02b
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-write-an-extension-method-visual-basic"></a>Como escrever um método de extensão (Visual Basic)
Métodos de extensão permitem adicionar métodos a uma classe existente. O método de extensão pode ser chamado como se fosse uma instância dessa classe.  
  
### <a name="to-define-an-extension-method"></a>Para definir um método de extensão  
  
1.  Abra um aplicativo novo ou existente do Visual Basic no Visual Studio.  
  
2.  Na parte superior do arquivo no qual você deseja definir um método de extensão, inclua a seguinte instrução import:  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  Dentro de um módulo em seu aplicativo novo ou existente, começar a definição do método com o atributo de extensão:  
  
    ```  
    <Extension()>  
    ```  
  
4.  Declare o método da maneira normal, exceto que o tipo do primeiro parâmetro deve ser do tipo de dados que você deseja estender.  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara um método de extensão no módulo `StringExtensions`. Um segundo módulo, `Module1`, importa `StringExtensions` e chama o método. O método de extensão deve estar no escopo quando ela é chamada. Método de extensão `PrintAndPunctuate` estende o <xref:System.String>classe com um método que exibe a instância de cadeia de caracteres, seguido por uma cadeia de caracteres de símbolos de pontuação enviados em como um parâmetro.</xref:System.String>  
  
```vb  
' Declarations will typically be in a separate module.  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
```vb  
' Import the module that holds the extension method you want to use,   
' and call it.  
  
Imports ConsoleApplication2.StringExtensions  
  
Module Module1  
  
    Sub Main()  
        Dim example = "Hello"  
        example.PrintAndPunctuate("?")  
        example.PrintAndPunctuate("!!!!")  
    End Sub  
  
End Module  
  
```  
  
 Observe que o método é definido com dois parâmetros e chamado com apenas um. O primeiro parâmetro, `aString`, no método definição está associada a `example`, a instância de `String` que chama o método. A saída do exemplo é da seguinte maneira:  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute></xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [Métodos de extensão](./extension-methods.md)   
 [Instrução Module](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
