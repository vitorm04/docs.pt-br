---
title: "Cláusula Group By (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
dev_langs:
- VB
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement
- Group By clause
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
caps.latest.revision: 20
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
ms.openlocfilehash: a40074c4602d6c0164c784d497fbfb134402bf62
ms.lasthandoff: 03/13/2017

---
# <a name="group-by-clause-visual-basic"></a>Cláusula Group By (Visual Basic)
Agrupa os elementos de um resultado de consulta. Também pode ser usado para aplicar funções de agregação para cada grupo. A operação de agrupamento é baseada em uma ou mais chaves.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a>Partes  
  
-   `listField1`, `listField2`  
  
     Opcional. Um ou mais campos de variável de consulta ou variáveis que identificam explicitamente os campos a serem incluídos no resultado agrupado. Se nenhum campo for especificado, todos os campos de variável de consulta ou variáveis são incluídos no resultado agrupado.  
  
-   `keyExp1`  
  
     Necessário. Uma expressão que identifica a chave a ser usada para determinar os grupos de elementos. Você pode especificar mais de uma chave para especificar uma chave composta.  
  
-   `keyExp2`  
  
     Opcional. Uma ou mais chaves adicionais que são combinadas com `keyExp1` para criar uma chave composta.  
  
-   `aggregateList`  
  
     Necessário. Uma ou mais expressões que identificam como os grupos são agregados. Para identificar um nome de membro para os resultados agrupados, use o `Group` palavra-chave, que pode estar em qualquer uma das seguintes formas:  
  
    ```  
    Into Group  
    ```  
  
     -ou-  
  
    ```  
    Into <alias> = Group  
    ```  
  
     Você também pode incluir funções agregadas para aplicar ao grupo.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o `Group By` cláusula para dividir os resultados de uma consulta em grupos. O agrupamento se baseia em uma chave ou uma chave composta que consiste em várias chaves. Elementos que estão associados com valores de chave correspondentes são incluídos no mesmo grupo.  
  
 Você usa o `aggregateList` parâmetro do `Into` cláusula e `Group` palavra-chave para identificar o nome do membro que é usado para fazer referência ao grupo. Você também pode incluir funções agregadas de `Into` cláusula para calcular valores para os elementos agrupados. Para obter uma lista de funções de agregação padrão, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir agrupa uma lista de clientes com base em sua localização (país) e fornece uma contagem dos clientes em cada grupo. Os resultados são ordenados pelo nome de país. Os resultados agrupados são ordenados pelo nome da cidade.  
  
 [!code-vb[VbSimpleQuerySamples n º&11;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [Cláusula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)
