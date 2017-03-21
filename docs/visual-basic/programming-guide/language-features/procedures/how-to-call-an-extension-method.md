---
title: "Como: chamar um método de extensão (Visual Basic) | Documentos do Microsoft"
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
- calling extension methods
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
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
ms.openlocfilehash: a7faf0eb36fee114d5fed914484c7c5cda0ae399
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Como chamar um método de extensão (Visual Basic)
Métodos de extensão permitem adicionar métodos a uma classe existente. Depois que um método de extensão é declarado e colocado no escopo, você pode chamá-lo como um método de instância do tipo que ele estende. Para obter mais informações sobre como escrever um método de extensão, consulte [como: gravar um método de extensão](./how-to-write-an-extension-method.md).  
  
 Consultem as instruções a seguir para o método de extensão `PrintAndPunctuate`, que exibirá a instância de cadeia de caracteres que o chama, seguido por qualquer valor que será enviada para o segundo parâmetro, `punc`.  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
  
```  
  
 O método deve estar no escopo quando ele é chamado.  
  
### <a name="to-call-an-extension-method"></a>Para chamar um método de extensão  
  
1.  Declare uma variável que tem o tipo de dados do primeiro parâmetro do método de extensão. Para `PrintAndPunctuate`, é necessário um <xref:System.String>variável:</xref:System.String>  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  Que variável invocará o método de extensão e seu valor é associado ao primeiro parâmetro, `aString`. Será exibida a seguinte instrução de chamada `Ready?`.  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     Observe que a chamada para esse método de extensão é apenas uma chamada para qualquer um dos, como o <xref:System.String>métodos que exigem um parâmetro da instância:</xref:System.String>  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  Declarar outra variável string e chame o método novamente para ver se ele funciona com qualquer cadeia de caracteres.  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     Dessa vez, o resultado é: `or not!!!`.  
  
## <a name="example"></a>Exemplo  
 O código a seguir é um exemplo completo da criação e uso de um método de extensão simples.  
  
```vb  
Imports System.Runtime.CompilerServices  
Imports ConsoleApplication1.StringExtensions  
  
Module Module1  
  
    Sub Main()  
  
        Dim example = "Hello"  
        example.PrintAndPunctuate(".")  
        example.PrintAndPunctuate("!!!!")  
  
        Dim example2 = "Goodbye"  
        example2.PrintAndPunctuate("?")  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
End Module  
  
' Output:  
' Hello.  
' Hello!!!!  
' Goodbye?  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como: gravar um método de extensão](./how-to-write-an-extension-method.md)   
 [Métodos de extensão](./extension-methods.md)   
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
