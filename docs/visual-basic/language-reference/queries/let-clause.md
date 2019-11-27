---
title: Cláusula Let
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 63eaf97016db259870eb77199651ecbdc5f809c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350428"
---
# <a name="let-clause-visual-basic"></a>Cláusula Let (Visual Basic)
Computa um valor e o atribui a uma nova variável dentro da consulta.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`variable`|Necessário. Um alias que pode ser usado para referenciar os resultados da expressão fornecida.|  
|`expression`|Necessário. Uma expressão que será avaliada e atribuída à variável especificada.|  
  
## <a name="remarks"></a>Comentários  
 A cláusula `Let` permite que você calcule valores para cada resultado da consulta e faça referência a eles usando um alias. O alias pode ser usado em outras cláusulas, como a cláusula `Where`. A cláusula `Let` permite que você crie uma instrução de consulta que seja mais fácil de ler, pois você pode especificar um alias para uma cláusula de expressão incluído na consulta e substituir o alias sempre que a cláusula de expressão for usada.  
  
 Você pode incluir qualquer número de atribuições de `variable` e `expression` na cláusula `Let`. Separe cada atribuição com uma vírgula (,).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir usa a cláusula `Let` para calcular um desconto de 10% nos produtos.  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
