---
title: Semântica nula
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: eb1e96ba44c5d64e8366a654c2d06d89c9b46c9a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172751"
---
# <a name="null-semantics"></a><span data-ttu-id="f1765-102">Semântica nula</span><span class="sxs-lookup"><span data-stu-id="f1765-102">Null Semantics</span></span>
<span data-ttu-id="f1765-103">A tabela a seguir fornece links para várias partes do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentação onde `null` (`Nothing` no Visual Basic) problemas são discutidos.</span><span class="sxs-lookup"><span data-stu-id="f1765-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="f1765-104">Tópico</span><span class="sxs-lookup"><span data-stu-id="f1765-104">Topic</span></span>|<span data-ttu-id="f1765-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1765-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f1765-106">Tipos incompatíveis CLR do SQL</span><span class="sxs-lookup"><span data-stu-id="f1765-106">SQL-CLR Type Mismatches</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|<span data-ttu-id="f1765-107">A seção "Semântica nula" neste tópico inclui a discussão sobre as três estado SQL booleano versus o dois estados common language runtime (CLR) <xref:System.Boolean>, o literal `Nothing` (Visual Basic) e `null` (C#) e outros semelhantes problemas.</span><span class="sxs-lookup"><span data-stu-id="f1765-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="f1765-108">Conversão de operador de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="f1765-108">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|<span data-ttu-id="f1765-109">“A seção de semântica nula” neste tópico descreve as semânticas nula de comparação em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f1765-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="f1765-110">Métodos de System.String</span><span class="sxs-lookup"><span data-stu-id="f1765-110">System.String Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|<span data-ttu-id="f1765-111">As “diferenças a seção .NET” neste tópico descrevem como um retorno de 0 de <xref:System.String.LastIndexOf%2A> pode significar qualquer pessoa que a cadeia de caracteres é nula ou que a posição encontrada é 0.</span><span class="sxs-lookup"><span data-stu-id="f1765-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="f1765-112">Calcular a soma dos valores em uma sequência numérica</span><span class="sxs-lookup"><span data-stu-id="f1765-112">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="f1765-113">Descreve como o <xref:System.Linq.Enumerable.Sum%2A> operador é avaliado como `null` (`Nothing` no Visual Basic) em vez de 0 para uma sequência que contém somente nulos ou para uma sequência vazia.</span><span class="sxs-lookup"><span data-stu-id="f1765-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1765-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1765-114">See also</span></span>

- [<span data-ttu-id="f1765-115">Funções e tipos de dados</span><span class="sxs-lookup"><span data-stu-id="f1765-115">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
