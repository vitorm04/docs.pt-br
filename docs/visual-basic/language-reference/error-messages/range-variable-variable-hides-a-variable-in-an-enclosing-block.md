---
title: "A variável de intervalo &lt;variável&gt; oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36633
- vbc36633
dev_langs:
- VB
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
caps.latest.revision: 5
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
ms.openlocfilehash: fd60c9503ca0c34a633b75a6ea08a8f1a6681b96
ms.lasthandoff: 03/13/2017

---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>A variável de intervalo &lt;variável&gt; oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta
Um nome de variável de intervalo especificado em uma `Select`, `From`, `Aggregate`, ou `Let` cláusula duplique o nome de uma variável de intervalo já especificado anteriormente na consulta, ou o nome de uma variável que é declarado implicitamente pela consulta, como um nome de campo ou o nome de uma função de agregação.  
  
 **ID do erro:** BC36633  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Verifique se todas as variáveis de alcance em um escopo de consulta em particular têm nomes exclusivos. Você pode delimitar a consulta entre parênteses para garantir que consultas aninhadas têm um escopo exclusivo.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Let](../../../visual-basic/language-reference/queries/let-clause.md)   
 [Cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
