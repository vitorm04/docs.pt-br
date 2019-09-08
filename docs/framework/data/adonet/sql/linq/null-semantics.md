---
title: Semântica nula
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: d0b18c0a699840d11f5e4add05147672f9bb69e9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792972"
---
# <a name="null-semantics"></a><span data-ttu-id="5acd9-102">Semântica nula</span><span class="sxs-lookup"><span data-stu-id="5acd9-102">Null Semantics</span></span>
<span data-ttu-id="5acd9-103">A tabela a seguir fornece links para várias partes da [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentação onde `null` os`Nothing` problemas (em Visual Basic) são discutidos.</span><span class="sxs-lookup"><span data-stu-id="5acd9-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="5acd9-104">Tópico</span><span class="sxs-lookup"><span data-stu-id="5acd9-104">Topic</span></span>|<span data-ttu-id="5acd9-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="5acd9-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5acd9-106">Tipos incompatíveis CLR do SQL</span><span class="sxs-lookup"><span data-stu-id="5acd9-106">SQL-CLR Type Mismatches</span></span>](sql-clr-type-mismatches.md)|<span data-ttu-id="5acd9-107">A seção "semântica nula" deste tópico inclui a discussão do booliano SQL de três Estados versus o <xref:System.Boolean>CLR (Common Language Runtime de dois Estados), o literal `Nothing` (Visual Basic) e `null` (C#) e outros semelhantes edições.</span><span class="sxs-lookup"><span data-stu-id="5acd9-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="5acd9-108">Conversão de operador de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="5acd9-108">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)|<span data-ttu-id="5acd9-109">“A seção de semântica nula” neste tópico descreve as semânticas nula de comparação em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5acd9-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="5acd9-110">Métodos de System.String</span><span class="sxs-lookup"><span data-stu-id="5acd9-110">System.String Methods</span></span>](system-string-methods.md)|<span data-ttu-id="5acd9-111">As “diferenças a seção .NET” neste tópico descrevem como um retorno de 0 de <xref:System.String.LastIndexOf%2A> pode significar qualquer pessoa que a cadeia de caracteres é nula ou que a posição encontrada é 0.</span><span class="sxs-lookup"><span data-stu-id="5acd9-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="5acd9-112">Calcular a soma dos valores em uma sequência numérica</span><span class="sxs-lookup"><span data-stu-id="5acd9-112">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="5acd9-113">Descreve como o <xref:System.Linq.Enumerable.Sum%2A> operador é avaliado como `null` (`Nothing` em Visual Basic) em vez de 0 para uma sequência que contém somente nulos ou para uma sequência vazia.</span><span class="sxs-lookup"><span data-stu-id="5acd9-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5acd9-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5acd9-114">See also</span></span>

- [<span data-ttu-id="5acd9-115">Funções e tipos de dados</span><span class="sxs-lookup"><span data-stu-id="5acd9-115">Data Types and Functions</span></span>](data-types-and-functions.md)
