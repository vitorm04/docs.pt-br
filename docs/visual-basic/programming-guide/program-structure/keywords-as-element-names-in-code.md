---
title: "Palavras-chave como nomes de elemento em c&#243;digo (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "nomes de elementos, código in"
  - "palavras-chave [Visual Basic], código in"
  - "conflitos de nome"
  - "código do Visual Basic, convenções de nomenclatura"
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Palavras-chave como nomes de elemento em c&#243;digo (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Qualquer elemento de programa \- como uma variável, classe, ou membro \- pode ter o mesmo nome que uma palavra chave restrita.  Por exemplo, você pode criar uma variável chamada `Loop`.  No entanto, para referir a sua versão disso \- que tem o mesmo nome que a palavra chave restrita `Loop` \- você deve ou precedê\-la com uma string de qualificação completa ou fechá\-la com colchetes \(`[ ]`\), como o seguinte exempo mostra.  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 Se você não faz nenhuma dessas opções, então o Visual Basic assume o uso da palavra chave intrínseca `Loop` e produz um erro, como no seguinte exemplo:  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 Você pode usar colchetes quando referir a formulários e controles, e quando declarando uma variável ou definindo um procedimento com o mesmo nome que uma palavra chave restrita.  É fácil esquecer de qualificar nomes ou incluir colchetes, e portanto introduzir erros em seu código e torná\-lo mais difícil de ler.  Por essa razão, recomendamos que você não use palavras chaves restritas como nomes de elementos de programas.  No entanto, se uma versão futura do Visual Basic definir uma nova palavra chave que conflite com um formulário existente ou nome de controle, você pode usar essa técnica quando atualizar seu código para funcionar na nova versão.  
  
> [!NOTE]
>  Seu programa também deve incluir nomes de elementeos fornecidos por outros assemblys referenciados.  Se esses nomes entrarem em conflito com palavras chavez restritas, então colocar colchetes em volta deles faz com que o Visual Basic os interprete como seus elementos definidos.  
  
## Consulte também  
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Estrutura do programa e convenções de código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Palavras\-chave](../../../visual-basic/language-reference/keywords/index.md)