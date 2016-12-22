---
title: "Cl&#225;usula Group By (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.QueryGroupByInto"
  - "vb.QueryGroupBy"
  - "vb.QueryGroupRef"
  - "vb.QueryGroupInto"
  - "vb.QueryGroup"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "consultas [Visual Basic], Group By"
  - "instrução Group By"
  - "cláusula Group By"
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cl&#225;usula Group By (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

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
  
     Obrigatório. Uma expressão que identifica a chave a ser usada para determinar os grupos de elementos. Você pode especificar mais de uma chave para especificar uma chave composta.  
  
-   `keyExp2`  
  
     Opcional. Uma ou mais chaves adicionais que são combinadas com `keyExp1` para criar uma chave composta.  
  
-   `aggregateList`  
  
     Obrigatório. Uma ou mais expressões que identificam como os grupos são agregados. Para identificar um nome de membro para os resultados agrupados, use o `Group` palavra-chave, que pode estar em qualquer uma das seguintes formas:  
  
    ```  
    Into Group  
    ```  
  
     - ou -  
  
    ```  
    Into <alias> = Group  
    ```  
  
     Você também pode incluir funções agregadas para aplicar ao grupo.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o `Group By` cláusula para dividir os resultados de uma consulta em grupos. O agrupamento se baseia em uma chave ou uma chave composta que consiste em várias chaves. Elementos que estão associados com valores de chave correspondentes são incluídos no mesmo grupo.  
  
 Você usa o `aggregateList` parâmetro do `Into` cláusula e `Group` palavra-chave para identificar o nome do membro que é usado para fazer referência ao grupo. Você também pode incluir funções agregadas de `Into` cláusula para calcular valores para os elementos agrupados. Para obter uma lista de funções de agregação padrão, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir agrupa uma lista de clientes com base em sua localização (país) e fornece uma contagem dos clientes em cada grupo. Os resultados são ordenados pelo nome de país. Os resultados agrupados são ordenados pelo nome da cidade.  
  
 [!code-vb[VbSimpleQuerySamples#11](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [Cláusula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)