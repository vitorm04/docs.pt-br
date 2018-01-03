---
title: "Semântica nula"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6786c7ea4441b1a753d6f0b4213f40fa64dcb4ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="null-semantics"></a><span data-ttu-id="fb0e3-102">Semântica nula</span><span class="sxs-lookup"><span data-stu-id="fb0e3-102">Null Semantics</span></span>
<span data-ttu-id="fb0e3-103">A tabela a seguir fornece links para diversas partes do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentação onde `null` (`Nothing` em [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) problemas são discutidos.</span><span class="sxs-lookup"><span data-stu-id="fb0e3-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) issues are discussed.</span></span>  
  
|<span data-ttu-id="fb0e3-104">Tópico</span><span class="sxs-lookup"><span data-stu-id="fb0e3-104">Topic</span></span>|<span data-ttu-id="fb0e3-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb0e3-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="fb0e3-106">Tipos incompatíveis CLR do SQL</span><span class="sxs-lookup"><span data-stu-id="fb0e3-106">SQL-CLR Type Mismatches</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|<span data-ttu-id="fb0e3-107">“A seção de semântica nula” neste tópico inclui o exame de três estado SQL booleano dois estados contra o Common Language Runtime (CLR) <xref:System.Boolean>, `Nothing` literal ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) e `null` (C#), e outros problemas semelhantes.</span><span class="sxs-lookup"><span data-stu-id="fb0e3-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="fb0e3-108">Conversão de operador de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="fb0e3-108">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|<span data-ttu-id="fb0e3-109">“A seção de semântica nula” neste tópico descreve as semânticas nula de comparação em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fb0e3-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="fb0e3-110">Métodos de System.String</span><span class="sxs-lookup"><span data-stu-id="fb0e3-110">System.String Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|<span data-ttu-id="fb0e3-111">As “diferenças a seção .NET” neste tópico descrevem como um retorno de 0 de <xref:System.String.LastIndexOf%2A> pode significar qualquer pessoa que a cadeia de caracteres é nula ou que a posição encontrada é 0.</span><span class="sxs-lookup"><span data-stu-id="fb0e3-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="fb0e3-112">Calcular a soma dos valores em uma sequência numérica</span><span class="sxs-lookup"><span data-stu-id="fb0e3-112">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="fb0e3-113">Descreve como o <xref:System.Linq.Enumerable.Sum%2A> operador é avaliada como `null` (`Nothing` em [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) em vez de 0 para uma sequência que contém apenas valores nulos ou para uma sequência vazia.</span><span class="sxs-lookup"><span data-stu-id="fb0e3-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb0e3-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb0e3-114">See Also</span></span>  
 [<span data-ttu-id="fb0e3-115">Funções e tipos de dados</span><span class="sxs-lookup"><span data-stu-id="fb0e3-115">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
