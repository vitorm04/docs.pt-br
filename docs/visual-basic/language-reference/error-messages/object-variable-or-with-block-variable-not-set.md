---
title: "Variável de objeto ou variável com bloco não definida"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e1f587e194acf744b6ec9b8f1bede3acef7b753
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-or-with-block-variable-not-set"></a>Variável de objeto ou variável com bloco não definida
Uma variável de objeto inválida está sendo referenciada.   Esse erro pode ocorrer por várias razões:  
  
-   Uma variável foi declarada sem especificar um tipo. Se uma variável é declarada sem especificar um tipo, o padrão é para o tipo `Object`.  
  
     Por exemplo, uma variável declarada com `Dim x` deve ser do tipo `Object;` uma variável declarada com `Dim x As String` deve ser do tipo `String`.  
  
    > [!TIP]
    >  O `Option Strict` instrução não permite digitar implícita que resulta em um `Object` tipo. Se você omitir o tipo, ocorrerá um erro de tempo de compilação. Consulte [opção Strict instrução](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
-   Você está tentando fazer referência a um objeto que foi definido como`Nothing`  
  
     .  
  
-   Você está tentando acessar um elemento de uma variável de matriz não foi declarado corretamente.  
  
     Por exemplo, uma matriz declarada como `products() As String` disparará o erro se você tentar fazer referência a um elemento da matriz `products(3) = "Widget"`. A matriz não tem elementos e é tratada como um objeto.  
  
-   Tentativa de acesso de código dentro de um `With...End With` bloquear antes que o bloco foi inicializado.   Um `With...End With` deve ser inicializado executando o `With` ponto de entrada de instrução.  
  
> [!NOTE]
>  Em versões anteriores do Visual Basic ou VBA esse erro também foi disparado, atribuindo um valor a uma variável sem usar o `Set` palavra-chave (`x = "name"` em vez de `Set x = "name"`). O `Set` palavra-chave não é válida no Visual Basic .net.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Definir `Option Strict` para `On` adicionando o código a seguir para o início do arquivo:  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  Se você não quiser habilitar `Option Strict`, pesquise o código para todas as variáveis que foram especificadas sem um tipo (`Dim x` em vez de `Dim x As String`) e adicione o tipo desejado para a declaração.  
  
3.  Verifique se você não está fazendo referência a uma variável de objeto que foi definida como `Nothing`.  Pesquise o código para a palavra-chave `Nothing`e revisar seu código para que o objeto não está definido como `Nothing` até após você ter referenciado.  
  
4.  Certifique-se de que quaisquer variáveis de matriz são dimensionadas para acessá-los. Você pode atribuir uma dimensão quando você cria a matriz (`Dim x(5) As String` em vez de `Dim x() As String`), ou use o `ReDim` palavra-chave para definir as dimensões da matriz antes de acessar pela primeira vez.  
  
5.  Certifique-se de sua `With` bloco é inicializado executando o `With` ponto de entrada de instrução.  
  
## <a name="see-also"></a>Consulte também  
 [Declaração de Variável do Objeto](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [Instrução With ... End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
