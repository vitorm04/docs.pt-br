---
title: "Resolução de sobrecarga de função (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cafbdd1a06ce506516fa985e9af147f55b4ea3d4
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="function-overload-resolution-entity-sql"></a>Resolução de sobrecarga de função (Entity SQL)
Este tópico descreve como as funções de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são resolvidas.  
  
 Mais de uma função pode ser definida com o mesmo nome, como as funções tenham assinaturas exclusivos.  
  
 Quando esse for o caso, os seguintes critérios devem ser aplicados para determinar que a função é referenciada por uma expressão fornecida. Esses critérios são aplicados em ordem. O primeiro critério que se aplica a uma única função é a função resolvida.  
  
1.  **O número do parâmetro**. A função tem o mesmo número de parâmetros especificados na expressão.  
  
2.  **Correspondência exata no tipo**. Cada tipo de argumento de função corresponde exatamente o tipo de parâmetro, ou é o literal nulo.  
  
3.  **Correspondência no subtipo**. Cada tipo de argumento corresponde exatamente de função ou subpropriedades é um tipo de parâmetro, ou o argumento é o literal nulo. Se várias funções diferem somente no número de conversões de tipo subpropriedades necessárias, a função com menos número de subpropriedades conversões de tipo é a função resolvida.  
  
4.  **Correspondência de promoção de tipo ou subtipo**. Cada tipo de argumento corresponde exatamente de função, é um tipo de subpropriedades, ou pode ser elevado ao tipo de parâmetro, ou o argumento é o literal nulo. Além disso, se várias funções diferem somente no número de conversões e de promoções de subpropriedades tipo, a função com menos número de subpropriedades conversões de tipo e as promoções a função é resolvida.  
  
 Se nenhum desses critérios resultam em uma única função que está sendo selecionada, a expressão de chamada de função é ambígua.  
  
 Mesmo se uma única função pode ser extraída usando essas regras, os argumentos ainda podem não corresponder os parâmetros. Um erro é gerado nesse caso.  
  
 Para funções definidas pelo usuário, a definição de uma função in-line de consulta tem precedência mesmo quando uma função o definida existe com uma assinatura que é uma correspondência melhor para a função definida pelo usuário.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Visão geral do Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Funções](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
