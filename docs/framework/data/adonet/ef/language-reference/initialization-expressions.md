---
title: Expressões de inicialização
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 352bda826c3b872d06252e168abfb1129f178bf8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762202"
---
# <a name="initialization-expressions"></a><span data-ttu-id="8a6c2-102">Expressões de inicialização</span><span class="sxs-lookup"><span data-stu-id="8a6c2-102">Initialization Expressions</span></span>
<span data-ttu-id="8a6c2-103">Uma expressão de inicialização inicializa um novo objeto.</span><span class="sxs-lookup"><span data-stu-id="8a6c2-103">An initialization expression initializes a new object.</span></span> <span data-ttu-id="8a6c2-104">A maioria das expressões de inicialização são suportadas, incluindo a maioria novo C# 3,0 e Visual Basic 9,0 expressões de inicialização.</span><span class="sxs-lookup"><span data-stu-id="8a6c2-104">Most initialization expressions are supported, including most new C# 3.0 and Visual Basic 9.0 initialization expressions.</span></span> <span data-ttu-id="8a6c2-105">Os seguintes tipos podem ser inicializados e retornado por uma consulta LINQ to Entities:</span><span class="sxs-lookup"><span data-stu-id="8a6c2-105">The following types can be initialized and returned by a LINQ to Entities query:</span></span>  
  
-   <span data-ttu-id="8a6c2-106">Uma coleção de zero ou mais objetos de entidade tipados ou uma projeção de tipos complexos que são definidos no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="8a6c2-106">A collection of zero or more typed entity objects or a projection of complex types that are defined in the conceptual model.</span></span>  
  
-   <span data-ttu-id="8a6c2-107">Tipos de CLR suportados por [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8a6c2-107">CLR types supported by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="8a6c2-108">Coleções internas.</span><span class="sxs-lookup"><span data-stu-id="8a6c2-108">Inline collections.</span></span>  
  
-   <span data-ttu-id="8a6c2-109">Tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="8a6c2-109">Anonymous types.</span></span>  
  
 <span data-ttu-id="8a6c2-110">A inicialização tipo anônimo é mostrada no exemplo a seguir na sintaxe da expressão de consulta:</span><span class="sxs-lookup"><span data-stu-id="8a6c2-110">Anonymous type initialization is shown in the following example in query expression syntax:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 <span data-ttu-id="8a6c2-111">O exemplo a seguir na sintaxe da consulta com base em método mostra a inicialização tipo anônimo:</span><span class="sxs-lookup"><span data-stu-id="8a6c2-111">The following example in method-based query syntax shows anonymous type initialization:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 <span data-ttu-id="8a6c2-112">A inicialização definido pelo usuário da classe também é suportado.</span><span class="sxs-lookup"><span data-stu-id="8a6c2-112">User-defined class initialization is also supported.</span></span> <span data-ttu-id="8a6c2-113">O padrão de inicialização C# 3,0 e Visual Basic 9,0 é suportado e pressupõe que o getter e o setter de propriedade são simétricos.</span><span class="sxs-lookup"><span data-stu-id="8a6c2-113">The C# 3.0 and Visual Basic 9.0 initialization pattern is supported and assumes that the property getter and setter are symmetric.</span></span> <span data-ttu-id="8a6c2-114">O exemplo a seguir na sintaxe da expressão de consulta a seguir mostra uma classe personalizada que está sendo inicializada na consulta:</span><span class="sxs-lookup"><span data-stu-id="8a6c2-114">The following example in query expression syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 <span data-ttu-id="8a6c2-115">O exemplo a seguir na sintaxe da consulta com base em método mostra uma classe personalizada que está sendo inicializada na consulta:</span><span class="sxs-lookup"><span data-stu-id="8a6c2-115">The following example in method-based query syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="8a6c2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a6c2-116">See Also</span></span>  
 [<span data-ttu-id="8a6c2-117">Expressões em consultas LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="8a6c2-117">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
