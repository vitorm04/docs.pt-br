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
ms.openlocfilehash: 46f59403feced4baafef4662065cb7daedbeaa7b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837072"
---
# <a name="visual-basic-naming-conventions"></a>Convenções de nomenclatura do Visual Basic
Quando você nomeia um elemento em seu aplicativo Visual Basic, o primeiro caractere do nome deve ser um caractere alfabético ou sublinhado. No entanto, observe que os nomes que começam com um sublinhado não são compatíveis com o [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 As sugestões a seguir se aplicam a nomenclatura.  
  
-   Inicie cada palavra separada um nome com uma letra maiuscula, como em `FindLastRecord` e `RedrawMyForm`.  
  
-   Comece nomes de função e método com um verbo, como em `InitNameArray` ou `CloseDialog`.  
  
-   Comece a classe, estrutura, módulo e nomes de propriedade com um substantivo, como em `EmployeeName` ou `CarAccessory`.  
  
-   Comece nomes de interface com o prefixo "I", seguido por um substantivo ou uma frase substantiva, como `IComponent`, ou com um adjetivo que descreve o comportamento da interface, como `IPersistable`. Não use o sublinhado e use abreviações com moderação, pois abreviações podem causar confusão.  
  
-   Comece nomes de manipulador de eventos com um substantivo que descreve o tipo de evento seguido de "`EventHandler`"sufixo, como em"`MouseEventHandler`".  
  
-   Em nomes de classes de argumento de evento, inclua o "`EventArgs`" sufixo.  
  
-   Se um evento tem um conceito de "antes" ou "after", use um sufixo no presente ou no passado, como em "`ControlAdd`"ou"`ControlAdded`".  
  
-   Para termos longos ou usados com frequência, use abreviações para manter os tamanhos de nome razoável, por exemplo, "HTML", em vez de "Hypertext Markup Language". Em geral, nomes de variáveis maiores do que 32 caracteres são difíceis de ler em um monitor definido para uma baixa resolução. Além disso, certifique-se de que suas abreviações são consistentes em todo o aplicativo. Alternar aleatoriamente em um projeto entre "HTML" e "Hypertext Markup Language" pode causar confusão.  
  
-   Evite usar nomes em um escopo interno que são os mesmos nomes em um escopo externo. Erros podem ocorrer se a variável errada é acessada. Se ocorrer um conflito entre uma variável e a palavra-chave do mesmo nome, você deve identificar a palavra-chave, precedendo-o com a biblioteca de tipo apropriado. Por exemplo, se você tiver uma variável chamada `Date`, você pode usar o intrínseco `Date` função apenas chamando <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- [Palavras-chave como Nomes de Elemento em Código](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Nomes de Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md)
