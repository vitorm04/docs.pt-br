---
title: "&#39; &lt;expressão&gt;&#39; não pode ser usado como restrição de tipo"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords: BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 054c05747491afb02601df00225a703560cbe91c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="39ltexpressiongt39-cannot-be-used-as-a-type-constraint"></a>&#39; &lt;expressão&gt;&#39; não pode ser usado como restrição de tipo
Uma lista de restrições inclui uma expressão que não representa uma restrição válida em um parâmetro de tipo.  
  
 Uma lista de restrições impõe exigências no tipo de argumento passado para o parâmetro de tipo. Você pode especificar os requisitos a seguir em qualquer combinação:  
  
-   O argumento de tipo deve implementar uma ou mais interfaces  
  
-   O argumento de tipo deve herdar de no máximo uma classe  
  
-   O argumento de tipo deve expor um construtor sem parâmetros que pode acessar o código de criação (incluem o `New` restrição)  
  
 Se você não incluir qualquer interface ou classe específica na lista de restrição, você pode impor uma necessidade de mais geral, especificando um destes procedimentos:  
  
-   O argumento de tipo deve ser um tipo de valor (incluem o `Structure` restrição)  
  
-   O argumento de tipo deve ser um tipo de referência (incluem o `Class` restrição)  
  
 Não é possível especificar `Structure` e `Class` para o mesmo tipo de parâmetro e você não pode especificar um mais de uma vez.  
  
 **ID do erro:** BC32061  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Verifique se a expressão e seus elementos estão escritos corretamente.  
  
-   Se a expressão não está qualificada para a lista anterior de requisitos, remova-o da lista de restrições.  
  
-   Se a expressão se refere a uma interface ou classe, verifique se o compilador tem acesso a essa interface ou classe. Talvez você precise qualificar seu nome, e talvez seja necessário adicionar uma referência ao seu projeto. Para obter mais informações, consulte "Referências a projetos" [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Tipos de Valor e Tipos de Referência](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [NIB: como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
