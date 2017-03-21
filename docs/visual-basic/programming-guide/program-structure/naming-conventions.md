---
title: "Convenções de nomenclatura do Visual Basic | Documentos do Microsoft"
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
- names, Visual Basic rules
- naming conventions
- naming conventions, Visual Basic
- Visual Basic code, naming conventions
- conventions, Visual Basic coding
- names, naming conventions
- naming conventions, classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
caps.latest.revision: 10
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
ms.openlocfilehash: 5d31bbe584b178a948332c84f1214b32e67d2631
ms.lasthandoff: 03/13/2017

---
# <a name="visual-basic-naming-conventions"></a>Convenções de nomenclatura do Visual Basic
Quando você nomeia um elemento em seu aplicativo Visual Basic, o primeiro caractere do nome deve ser um caractere alfabético ou um sublinhado. Observe, entretanto, que nomes que começam com um sublinhado não são compatíveis com o [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS).  
  
 As sugestões a seguir se aplicam à nomeação.  
  
-   Inicie cada palavra separada um nome com uma letra maiuscula, como em `FindLastRecord` e `RedrawMyForm`.  
  
-   Comece nomes de função e método com um verbo, como em `InitNameArray` ou `CloseDialog`.  
  
-   Comece a classe, estrutura, módulo e nomes de propriedade com um substantivo, como em `EmployeeName` ou `CarAccessory`.  
  
-   Inicie nomes de interfaces com o prefixo "I", seguido por um substantivo ou uma frase substantiva, como `IComponent`, ou com um adjetivo que descreve o comportamento da interface, como `IPersistable`. Não use o sublinhado e use abreviações com parcimônia, porque as abreviações podem causar confusão.  
  
-   Comece nomes de manipuladores de eventos com um substantivo que descreve o tipo de evento seguido de "`EventHandler`"sufixo, como em"`MouseEventHandler`".  
  
-   Em nomes de classes de argumento de evento, inclua o "`EventArgs`" sufixo.  
  
-   Se um evento possui um conceito de "antes" ou "depois", use um sufixo no presente ou no passado, como em "`ControlAdd`"ou"`ControlAdded`".  
  
-   Para termos longos ou usados com frequência, use abreviações para manter comprimentos de nome razoáveis, por exemplo, "HTML", em vez de "Hypertext Markup Language". Em geral, nomes de variáveis com mais de 32 caracteres são difíceis de ler em um monitor definido para uma resolução baixa. Além disso, certifique-se de que suas abreviações são consistentes em todo o aplicativo. Alternar aleatoriamente em um projeto entre "HTML" e "Hypertext Markup Language" pode levar a confusão.  
  
-   Evite usar nomes em um escopo interno que sejam os mesmos nomes em um escopo externo. Erros podem ocorrer se a variável errada é acessada. Se ocorrer um conflito entre uma variável e a palavra-chave de mesmo nome, você deve identificar a palavra-chave precedendo-o com a biblioteca de tipo apropriado. Por exemplo, se você tiver uma variável chamada `Date`, você pode usar o intrínseco `Date` função chamando <xref:System.DateTime.Date%2A?displayProperty=fullName>.</xref:System.DateTime.Date%2A?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 [Palavras-chave como nomes de elementos em código](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)   
 [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Estrutura do programa e convenções de código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md)
