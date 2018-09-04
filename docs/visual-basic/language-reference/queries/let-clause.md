---
title: Cláusula Let (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 34c0fd239d9e08dab4a107cb8447941e7ab3ecbe
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516757"
---
# <a name="let-clause-visual-basic"></a>Cláusula Let (Visual Basic)
Calcula um valor e o atribui a uma nova variável dentro da consulta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`variable`|Necessário. Um alias que pode ser usado para referenciar os resultados da expressão fornecida.|  
|`expression`|Necessário. Uma expressão que será avaliada e atribuída à variável especificada.|  
  
## <a name="remarks"></a>Comentários  
 O `Let` cláusula permite que você calcule valores para cada resultado da consulta e referenciá-los usando um alias. O alias pode ser usado em outras cláusulas, como o `Where` cláusula. O `Let` cláusula permite que você crie uma instrução de consulta que é mais fácil de ler porque você pode especificar um alias para uma cláusula de expressão incluída na consulta e substituir o alias de cada vez que a cláusula de expressão é usada.  
  
 Você pode incluir qualquer número de `variable` e `expression` atribuições no `Let` cláusula. Separe cada atribuição com uma vírgula (,).  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de código usa o `Let` cláusula para 10% de desconto em produtos de computação.  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Consultas](../../../visual-basic/language-reference/queries/index.md)  
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
