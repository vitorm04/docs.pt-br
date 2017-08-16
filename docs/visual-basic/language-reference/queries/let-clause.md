---
title: "Cláusula Let (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryLet
dev_langs:
- VB
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause
- Let statement
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
caps.latest.revision: 16
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
ms.openlocfilehash: 0345db041e4e8fbeb14b295b8f03500d450da087
ms.lasthandoff: 03/13/2017

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
 O `Let` cláusula permite que você calcule valores para cada resultado de consulta e referência-los usando um alias. O alias pode ser usado em outras cláusulas, como o `Where` cláusula. O `Let` cláusula permite que você crie uma instrução de consulta que é mais fácil de ler, pois você pode especificar um alias para uma cláusula de expressão incluída na consulta e substituir o alias cada vez que a cláusula de expressão for usada.  
  
 Você pode incluir qualquer número de `variable` e `expression` atribuições de `Let` cláusula. Separe cada atribuição com uma vírgula (,).  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de código usa o `Let` cláusula para calcular 10% de desconto em produtos.  
  
 [!code-vb[VbSimpleQuerySamples n º&16;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
