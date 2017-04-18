---
title: "&quot;&lt;expressão&gt;&quot; não pode ser usado como restrição de tipo | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32061
- vbc32061
dev_langs:
- VB
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: ae3e2be6fd404db6eea398b8ec9b45b3b778624c
ms.lasthandoff: 03/13/2017

---
# <a name="39ltexpressiongt39-cannot-be-used-as-a-type-constraint"></a>'&lt;expressão&gt;' não pode ser usado como restrição de tipo
Uma lista de restrições inclui uma expressão que não representa uma restrição válida em um parâmetro de tipo.  
  
 Uma lista de restrições impõe exigências no tipo de argumento passado para o parâmetro de tipo. Você pode especificar os seguintes requisitos em qualquer combinação:  
  
-   O argumento de tipo deve implementar uma ou mais interfaces  
  
-   O argumento de tipo deve herdar de no máximo uma classe  
  
-   O argumento de tipo deve expor um construtor sem parâmetros que pode acessar o código de criação (incluem o `New` restrição)  
  
 Se você não incluir qualquer interface ou classe específica na lista de restrição, você pode impor uma necessidade geral, especificando um destes procedimentos:  
  
-   O argumento de tipo deve ser um tipo de valor (inclua a `Structure` restrição)  
  
-   O argumento de tipo deve ser um tipo de referência (incluem o `Class` restrição)  
  
 Não é possível especificar `Structure` e `Class` para o mesmo tipo de parâmetro e você não pode especificar uma mais de uma vez.  
  
 **ID do erro:** BC32061  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Verifique se a expressão e seus elementos estão escritos corretamente.  
  
-   Se a expressão não está qualificada para a lista anterior de requisitos, remova-o da lista de restrições.  
  
-   Se a expressão fizer referência a uma interface ou classe, verifique se o compilador tem acesso a essa interface ou classe. Talvez você precise qualificar seu nome, e talvez seja necessário adicionar uma referência ao seu projeto. Para obter mais informações, consulte "Referências a projetos" [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Tipos de valor e tipos de referência](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [NIB: como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
