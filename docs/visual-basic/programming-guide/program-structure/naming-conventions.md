---
title: Convenções de nomenclatura
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
ms.openlocfilehash: 98fdda2934c9df1b33f41b6e0442a39246efe168
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347316"
---
# <a name="visual-basic-naming-conventions"></a>Convenções de nomenclatura do Visual Basic
Quando você nomear um elemento em seu aplicativo Visual Basic, o primeiro caractere desse nome deverá ser um caractere alfabético ou um sublinhado. Observe, no entanto, que os nomes que começam com um sublinhado não são compatíveis com a [independência de idioma e com os componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 As sugestões a seguir se aplicam à nomenclatura.  
  
- Comece cada palavra separada em um nome com uma letra maiúscula, como em `FindLastRecord` e `RedrawMyForm`.  
  
- Inicie os nomes de função e método com um verbo, como em `InitNameArray` ou `CloseDialog`.  
  
- Comece os nomes de classe, estrutura, módulo e propriedade com um substantivo, como em `EmployeeName` ou `CarAccessory`.  
  
- Comece os nomes de interface com o prefixo "I", seguido por um substantivo ou uma frase substantivo, como `IComponent`, ou com um adjetivo que descreve o comportamento da interface, como `IPersistable`. Não use o sublinhado e use abreviações com moderação, pois as abreviações podem causar confusão.  
  
- Inicie os nomes do manipulador de eventos com um substantivo que descreve o tipo de evento seguido pelo sufixo "`EventHandler`", como em "`MouseEventHandler`".  
  
- Em nomes de classes de argumento de evento, inclua o sufixo "`EventArgs`".  
  
- Se um evento tiver um conceito de "antes" ou "depois", use um sufixo no conjugação presente ou anterior, como em "`ControlAdd`" ou "`ControlAdded`".  
  
- Para termos longos ou usados com frequência, use abreviações para manter os comprimentos de nome razoáveis, por exemplo, "HTML", em vez de "linguagem HTML". Em geral, é difícil ler nomes de variáveis com mais de 32 caracteres em um monitor definido como uma baixa resolução. Além disso, verifique se suas abreviações são consistentes em todo o aplicativo. Alternar aleatoriamente em um projeto entre "HTML" e "linguagem HTML" pode levar à confusão.  
  
- Evite usar nomes em um escopo interno que sejam iguais aos nomes em um escopo externo. Os erros poderão ocorrer se a variável incorreta for acessada. Se ocorrer um conflito entre uma variável e a palavra-chave de mesmo nome, você deverá identificar a palavra-chave precedendo-a à biblioteca de tipos apropriada. Por exemplo, se você tiver uma variável chamada `Date`, poderá usar a função intrínseca `Date` apenas chamando <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- [Palavras-chave como Nomes de Elemento em Código](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Nomes de Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md)
