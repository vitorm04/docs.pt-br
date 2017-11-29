---
title: "Expressões constantes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 759805b2970aa760e4bce882789efbc947303573
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="constant-expressions"></a>Expressões constantes
Uma expressão constante consiste em um valor constante. Os valores constantes são convertidos diretamente às expressões constantes da árvore de comando, sem nenhuma conversão no cliente. Isso inclui as expressões que levam a um valor constante. Portanto, o comportamento da fonte de dados deve ser esperado para todas as expressões que envolvem constantes. Isso pode levar ao comportamento que difere do comportamento de CLR.  
  
 O exemplo a seguir mostra uma expressão constante que é avaliada no servidor.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] não oferece suporte usando uma classe de usuário como uma constante. No entanto, uma referência de propriedade em uma classe de usuário é considerada uma constante, e será convertida em uma expressão constante de árvore de comando e executada na fonte de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Expressões em consultas LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
