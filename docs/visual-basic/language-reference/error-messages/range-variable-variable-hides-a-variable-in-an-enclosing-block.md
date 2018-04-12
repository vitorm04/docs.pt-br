---
title: Variável de intervalo &lt;variável&gt; oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ccbac48694a13daa09f2511cf39d5dbd51cdaaf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>Variável de intervalo &lt;variável&gt; oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta
Um nome de variável de intervalo especificado em uma `Select`, `From`, `Aggregate`, ou `Let` cláusula igual ao nome de uma variável de intervalo já especificado anteriormente na consulta, ou o nome de uma variável que é declarado implicitamente pela consulta, como um nome de campo ou o nome de uma função de agregação.  
  
 **ID do erro:** BC36633  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Certifique-se de que todas as variáveis de intervalo em um escopo de consulta em particular têm nomes exclusivos. Você pode colocar uma consulta entre parênteses para garantir que consultas aninhadas têm um escopo único.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Cláusula Let](../../../visual-basic/language-reference/queries/let-clause.md)  
 [Cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
