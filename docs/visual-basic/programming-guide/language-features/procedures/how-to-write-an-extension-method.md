---
title: "Como escrever um m&#233;todo de extens&#227;o (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "estendendo tipos de dados"
  - "métodos de extensão [Visual Basic]"
  - "métodos de extensão de gravação"
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como escrever um m&#233;todo de extens&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Métodos de extensão permitem que você adicionar métodos a uma classe existente.  O método de extensão pode ser chamado como se fosse uma instância dessa classe.  
  
### Para definir um método de extensão  
  
1.  Abra um aplicativo de Visual Basic de novo ou existente no Visual Studio.  
  
2.  Na parte superior do arquivo no qual você deseja definir um método de extensão, inclua a seguinte instrução de importação:  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  Dentro de um módulo em seu aplicativo de novo ou existente, começa a definição do método com o atributo de extensão:  
  
    ```  
    <Extension()>  
    ```  
  
4.  Declare seu método da maneira comum, exceto pelo fato do tipo do primeiro parâmetro deve ser o tipo de dados que você deseja estender.  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## Exemplo  
 O exemplo a seguir declara um método de extensão no módulo `StringExtensions`.  Um segundo módulo, `Module1`, importa `StringExtensions` e chama o método.  O método de extensão deve estar no escopo quando ele é chamado.  Método de extensão `PrintAndPunctuate` estende o <xref:System.String> classe com um método que exibe a ocorrência de string é seguido por uma seqüência de caracteres de símbolos de pontuação enviada em como um parâmetro.  
  
```vb#  
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
  
```vb#  
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
  
 Observe que o método é definido com dois parâmetros e chamado com apenas um.  O primeiro parâmetro, `aString`, no método definição está vinculada a `example`, a instância do `String` que chama o método.  A saída do exemplo é o seguinte:  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## Consulte também  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [Métodos de extensão](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)   
 [Instrução Module](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)