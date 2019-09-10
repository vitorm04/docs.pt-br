---
title: Expressões de inicialização
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 5d6656ab77f7ad0f7366a230d98b95cff5b2677b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854437"
---
# <a name="initialization-expressions"></a>Expressões de inicialização
Uma expressão de inicialização inicializa um novo objeto. A maioria das expressões de inicialização são suportadas, incluindo a maioria novo C# 3,0 e Visual Basic 9,0 expressões de inicialização. Os seguintes tipos podem ser inicializados e retornado por uma consulta LINQ to Entities:  
  
- Uma coleção de zero ou mais objetos de entidade tipados ou uma projeção de tipos complexos que são definidos no modelo conceitual.  
  
- Tipos CLR com suporte no Entity Framework.
  
- Coleções internas.  
  
- Tipos anônimos.  
  
 A inicialização tipo anônimo é mostrada no exemplo a seguir na sintaxe da expressão de consulta:  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 O exemplo a seguir na sintaxe da consulta com base em método mostra a inicialização tipo anônimo:  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 A inicialização definido pelo usuário da classe também é suportado. O padrão de inicialização C# 3,0 e Visual Basic 9,0 é suportado e pressupõe que o getter e o setter de propriedade são simétricos. O exemplo a seguir na sintaxe da expressão de consulta a seguir mostra uma classe personalizada que está sendo inicializada na consulta:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 O exemplo a seguir na sintaxe da consulta com base em método mostra uma classe personalizada que está sendo inicializada na consulta:  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a>Consulte também

- [Expressões em consultas LINQ to Entities](expressions-in-linq-to-entities-queries.md)
