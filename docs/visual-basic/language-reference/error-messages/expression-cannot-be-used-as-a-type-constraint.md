---
title: "&#39;&lt;expression&gt;&#39; n&#227;o pode ser usado como restri&#231;&#227;o de tipo | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32061"
  - "vbc32061"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32061"
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;expression&gt;&#39; n&#227;o pode ser usado como restri&#231;&#227;o de tipo
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma lista de restrições inclui uma expressão que não representa uma restrição válida em um parâmetro de tipo.  
  
 Uma lista de restrições impõe exigências no tipo de argumento passado ao tipo de parâmetro.  Você pode especificar as seguintes exigências em qualquer combinação:  
  
-   O argumento de tipo deve implementar uma ou mais interfaces  
  
-   O argumento de digitação deve herdar de, no máximo, uma classe.  
  
-   O argumento de tipo deve expor um construtor sem\-parâmetros que o código criador possa acessar \(incluindo a restrição `New`\)  
  
 Se você não incluir qualquer interface ou classe específica na lista de restrição, você pode impor uma necessidade geral, especificando um destes procedimentos:  
  
-   O tipo de argumento deve ser um tipo de valor \(inclua a restrição `Structure`\)  
  
-   O tipo de argumento deve ser um tipo de referência \(inclua a restrição `Class`\)  
  
 Não é possível especificar ambos, `Structure` e `Class`, para o mesmo parâmetro de tipo e você não pode especificar qualquer deles mais de uma vez.  
  
 **Identificação do erro:**  BC32061  
  
### Para corrigir este erro  
  
-   Verifique se a expressão e seus elementos estão escritos corretamente.  
  
-   Se a expressão não está qualificada para obter a lista anterior de requisitos, remova\-a da lista de restrições.  
  
-   Se a expressão fizer referência a uma interface ou classe, verifique se o compilador tem acesso a essa interface ou classe.  Talvez você precise qualificar seu nome, e você talvez precise adicionar uma referência ao seu projeto.  Para obter mais informações, consulte "Referências a projetos " no [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Tipos de valor e referência](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)