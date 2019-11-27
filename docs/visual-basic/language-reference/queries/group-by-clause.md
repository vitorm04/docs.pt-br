---
title: Cláusula Group By
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement [Visual Basic]
- Group By clause [Visual Basic]
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
ms.openlocfilehash: 87080254ad5d237a593f0c35e7c3fdaef3a8ad59
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350470"
---
# <a name="group-by-clause-visual-basic"></a>Cláusula Group By (Visual Basic)
Agrupa os elementos de um resultado de consulta. Também pode ser usado para aplicar funções de agregação a cada grupo. A operação de agrupamento é baseada em uma ou mais chaves.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a>Partes  
  
- `listField1`, `listField2`  
  
     Opcional. Um ou mais campos da variável de consulta ou variáveis que identificam explicitamente os campos a serem incluídos no resultado agrupado. Se nenhum campo for especificado, todos os campos da variável de consulta ou variáveis serão incluídos no resultado agrupado.  
  
- `keyExp1`  
  
     Necessária. Uma expressão que identifica a chave a ser usada para determinar os grupos de elementos. Você pode especificar mais de uma chave para especificar uma chave composta.  
  
- `keyExp2`  
  
     Opcional. Uma ou mais chaves adicionais que são combinadas com `keyExp1` para criar uma chave composta.  
  
- `aggregateList`  
  
     Necessária. Uma ou mais expressões que identificam como os grupos são agregados. Para identificar um nome de membro para os resultados agrupados, use a palavra-chave `Group`, que pode estar em qualquer uma das seguintes formas:  
  
    ```vb  
    Into Group  
    ```  
  
     - ou -  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     Você também pode incluir funções de agregação para aplicar ao grupo.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar a cláusula `Group By` para dividir os resultados de uma consulta em grupos. O agrupamento é baseado em uma chave ou em uma chave composta que consiste em várias chaves. Os elementos associados aos valores de chave correspondentes são incluídos no mesmo grupo.  
  
 Use o parâmetro `aggregateList` da cláusula `Into` e a palavra-chave `Group` para identificar o nome do membro que é usado para fazer referência ao grupo. Você também pode incluir funções de agregação na cláusula `Into` para computar valores para os elementos agrupados. Para obter uma lista de funções de agregação padrão, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir agrupa uma lista de clientes com base em seu local (país/região) e fornece uma contagem dos clientes em cada grupo. Os resultados são ordenados por nome de país/região. Os resultados agrupados são ordenados por nome de cidade.  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Cláusula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)
