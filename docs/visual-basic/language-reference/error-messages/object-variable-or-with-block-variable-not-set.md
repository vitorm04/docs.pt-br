---
title: Variável de objeto ou variável com bloco não definida
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: b2c0c47b359e218111c1629ea574303a6d663046
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297922"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>Variável de objeto ou variável com bloco não definida
Uma variável de objeto inválido está sendo referenciada.   Esse erro pode ocorrer por várias razões:  
  
-   Uma variável foi declarada sem especificar um tipo. Se uma variável é declarada sem especificar um tipo, ele assume como padrão para o tipo `Object`.  
  
     Por exemplo, uma variável declarada com `Dim x` seria do tipo `Object;` uma variável declarada com `Dim x As String` seria do tipo `String`.  
  
    > [!TIP]
    >  O `Option Strict` instrução não permite digitação implícita que resulta em um `Object` tipo. Se você omitir o tipo, ocorrerá um erro de tempo de compilação. Ver [opção Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
-   Você está tentando fazer referência a um objeto que foi definido como `Nothing`  
  
     .  
  
-   Você está tentando acessar um elemento de uma variável de matriz não foi declarada corretamente.  
  
     Por exemplo, uma matriz declarada como `products() As String` disparará o erro se você tentar fazer referência a um elemento da matriz `products(3) = "Widget"`. A matriz não tem nenhum elemento e é tratada como um objeto.  
  
-   Você está tentando fazer o código de acesso dentro de um `With...End With` bloquear antes do bloco foi inicializado.   Um `With...End With` deve ser inicializado, executando o `With` ponto de entrada de instrução.  
  
> [!NOTE]
>  Em versões anteriores do Visual Basic ou VBA esse erro também foi disparado, atribuindo um valor a uma variável sem usar o `Set` palavra-chave (`x = "name"` em vez de `Set x = "name"`). O `Set` palavra-chave não é mais válida no Visual Basic .net.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Definir `Option Strict` para `On` , adicionando o seguinte código ao início do arquivo:  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2. Se você não quiser habilitar `Option Strict`, pesquise o código para todas as variáveis que foram especificadas sem um tipo (`Dim x` em vez de `Dim x As String`) e adicione o tipo desejado para a declaração.  
  
3. Verifique se você não está fazendo referência a uma variável de objeto que foi definida como `Nothing`.  Pesquise o código para a palavra-chave `Nothing`e revisar seu código para que o objeto não está definido como `Nothing` até após você ter referenciado.  
  
4. Certifique-se de que todas as variáveis de matriz são dimensionadas antes de você acessá-los. Você pode atribuir uma dimensão quando você cria a matriz (`Dim x(5) As String` em vez de `Dim x() As String`), ou usar o `ReDim` palavra-chave para definir as dimensões da matriz antes de acessar pela primeira vez.  
  
5. Certifique-se de sua `With` bloco é inicializado executando o `With` ponto de entrada de instrução.  
  
## <a name="see-also"></a>Consulte também

- [Declaração de Variável do Objeto](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Instrução With ... End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
