---
title: "Variável de objeto ou variável com bloco não definida | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID91
dev_langs:
- VB
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
caps.latest.revision: 9
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 820ef0115a6a27d77f10f4e41d95576bbd79bfa3
ms.lasthandoff: 03/13/2017

---
# <a name="object-variable-or-with-block-variable-not-set"></a>Variável de objeto ou variável com bloco não definida
Uma variável de objeto inválida está sendo referenciada.   Esse erro pode ocorrer por várias razões:  
  
-   Uma variável foi declarada sem especificar um tipo. Se uma variável é declarada sem especificar um tipo, ele assume como padrão para o tipo `Object`.  
  
     Por exemplo, uma variável declarada com `Dim x` deve ser do tipo `Object;` uma variável declarada com `Dim x As String` deve ser do tipo `String`.  
  
    > [!TIP]
    >  O `Option Strict` instrução não permite a digitação implícita que resulta em um `Object` tipo. Se você omitir o tipo, ocorrerá um erro de tempo de compilação. Consulte [opção Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
-   Você está tentando fazer referência a um objeto que foi definido como`Nothing`  
  
     .  
  
-   Você está tentando acessar um elemento de uma variável de matriz não foi declarado corretamente.  
  
     Por exemplo, uma matriz declarada como `products() As String` irá disparar o erro se você tentar fazer referência a um elemento da matriz `products(3) = "Widget"`. A matriz não tem elementos e é tratada como um objeto.  
  
-   Tentativa de acesso de código dentro de um `With...End With` bloquear antes que o bloco foi inicializado.   A `With...End With` deve ser inicializado executando o `With` ponto de entrada da declaração.  
  
> [!NOTE]
>  Em versões anteriores do Visual Basic ou VBA esse erro também foi disparado, atribuindo um valor a uma variável sem usar o `Set` palavra-chave (`x = "name"` em vez de `Set x = "name"`). O `Set` palavra-chave não é válido no Visual Basic .net.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Definir `Option Strict` para `On` , adicionando o seguinte código ao início do arquivo:  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  Se você não quiser habilitar `Option Strict`, pesquise o código para todas as variáveis que foram especificadas sem um tipo (`Dim x` em vez de `Dim x As String`) e adicione o tipo desejado para a declaração.  
  
3.  Verifique se você não está fazendo referência a uma variável de objeto que foi definida como `Nothing`.  Pesquise o código para a palavra-chave `Nothing`e revisar seu código para que o objeto não está definida como `Nothing` até que, depois de você ter referenciado.  
  
4.  Certifique-se de que quaisquer variáveis de matriz são dimensionadas para acessá-los. É possível atribuir uma dimensão quando você cria a matriz (`Dim x(5) As String` em vez de `Dim x() As String`), ou use o `ReDim` palavra-chave para definir as dimensões da matriz antes de acessar pela primeira vez.  
  
5.  Verifique se o `With` bloco é inicializado executando o `With` ponto de entrada da declaração.  
  
## <a name="see-also"></a>Consulte também  
 [Declaração de variável de objeto](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Instrução reDim](../../../visual-basic/language-reference/statements/redim-statement.md)   
 [Instrução With ... End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
