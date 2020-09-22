---
title: A variável de intervalo <variable> oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: d7399e7f51dc7c00ed903fa74647038009433ac0
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870920"
---
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>A variável de intervalo \<variable> oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta

Um nome de variável de intervalo especificado em uma `Select` cláusula,, `From` `Aggregate` ou `Let` duplica o nome de uma variável de intervalo já especificada anteriormente na consulta ou o nome de uma variável que é implicitamente declarada pela consulta, como um nome de campo ou o nome de uma função de agregação.  
  
 **ID do erro:** BC36633  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Verifique se todas as variáveis de intervalo em um determinado escopo de consulta têm nomes exclusivos. Você pode colocar uma consulta entre parênteses para garantir que as consultas aninhadas tenham um escopo exclusivo.  
  
## <a name="see-also"></a>Confira também

- [Introdução a LINQ no Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Cláusula from](../queries/from-clause.md)
- [Cláusula Let](../queries/let-clause.md)
- [Cláusula Aggregate](../queries/aggregate-clause.md)
- [Cláusula SELECT](../queries/select-clause.md)
