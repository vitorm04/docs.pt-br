---
title: A variável de intervalo <variable> oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: 8d898d2d3c5f36177a6363c1a24940fe46de83d3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259860"
---
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>Variável de intervalo \<variável > oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta
Um nome de variável de intervalo especificado em uma `Select`, `From`, `Aggregate`, ou `Let` cláusula duplique o nome de uma variável de intervalo já especificado anteriormente na consulta ou o nome de uma variável que é declarado implicitamente pela consulta, como um nome de campo ou o nome de uma função de agregação.  
  
 **ID do erro:** BC36633  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Certifique-se de que todas as variáveis de intervalo em um escopo de consulta em particular tenham nomes exclusivos. Você pode colocar uma consulta entre parênteses para garantir que as consultas aninhadas têm um escopo exclusivo.  
  
## <a name="see-also"></a>Consulte também
- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Let](../../../visual-basic/language-reference/queries/let-clause.md)
- [Cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
