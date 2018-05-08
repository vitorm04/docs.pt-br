---
title: Convenções de nomenclatura do Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: cb7e9f2a577e95e09fde885df1a78aea4e7fa466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="visual-basic-naming-conventions"></a>Convenções de nomenclatura do Visual Basic
Quando você nomeia um elemento em seu aplicativo do Visual Basic, o primeiro caractere do nome deve ser um caractere alfabético ou um sublinhado. No entanto, observe que os nomes que começam com um sublinhado não são compatíveis com o [independência da linguagem e componentes independentes da linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 As sugestões a seguir se aplicam a nomenclatura.  
  
-   Inicie cada palavra separada um nome com uma letra maiuscula, como em `FindLastRecord` e `RedrawMyForm`.  
  
-   Comece nomes de função e método com um verbo, como em `InitNameArray` ou `CloseDialog`.  
  
-   Comece a classe, estrutura, módulo e nomes de propriedade com um substantivo, como em `EmployeeName` ou `CarAccessory`.  
  
-   Comece nomes de interface com o prefixo "I", seguido por um substantivo ou locução, como `IComponent`, ou com um adjetivo que descreve o comportamento da interface, como `IPersistable`. Não use o caractere de sublinhado e use abreviações com moderação, pois as abreviações podem causar confusão.  
  
-   Comece nomes de manipuladores de eventos com um substantivo que descreve o tipo de evento seguido de "`EventHandler`"sufixo, como em"`MouseEventHandler`".  
  
-   Em nomes de classes de argumento de evento, inclua o "`EventArgs`" sufixo.  
  
-   Se um evento tem um conceito de "antes" ou "depois", use um sufixo no presente ou no passado, como em "`ControlAdd`"ou"`ControlAdded`".  
  
-   Para termos longos ou usados com frequência, use abreviações para manter comprimentos de nome razoável, por exemplo, "HTML", em vez de "HTML". Em geral, os nomes de variável é maiores do que 32 caracteres são difíceis de ler em um monitor definido com uma resolução baixa. Além disso, certifique-se de que suas abreviações são consistentes em todo o aplicativo. Alternar aleatoriamente em um projeto entre "HTML" e "HTML" pode causar confusão.  
  
-   Evite usar nomes em um escopo interno que são os mesmos nomes em um escopo externo. Erros podem ocorrer se a variável errada é acessada. Se ocorrer um conflito entre uma variável e a palavra-chave do mesmo nome, você deve identificar a palavra-chave precedendo-as com a biblioteca de tipo apropriado. Por exemplo, se você tiver uma variável chamada `Date`, você pode usar o intrínseco `Date` função apenas chamando <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também  
 [Palavras-chave como Nomes de Elemento em Código](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Nomes de Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md)
