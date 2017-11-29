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
ms.openlocfilehash: 3820b1282dda4155946ff22784e5ebe18525b45c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="null-semantics"></a><span data-ttu-id="229f7-102">Semântica nula</span><span class="sxs-lookup"><span data-stu-id="229f7-102">Null Semantics</span></span>
<span data-ttu-id="229f7-103">A tabela a seguir fornece links para diversas partes do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentação onde `null` (`Nothing` em [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) problemas são discutidos.</span><span class="sxs-lookup"><span data-stu-id="229f7-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) issues are discussed.</span></span>  
  
|<span data-ttu-id="229f7-104">Tópico</span><span class="sxs-lookup"><span data-stu-id="229f7-104">Topic</span></span>|<span data-ttu-id="229f7-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="229f7-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="229f7-106">Incompatibilidade de tipo CLR do SQL</span><span class="sxs-lookup"><span data-stu-id="229f7-106">SQL-CLR Type Mismatches</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|<span data-ttu-id="229f7-107">“A seção de semântica nula” neste tópico inclui o exame de três estado SQL booleano dois estados contra o Common Language Runtime (CLR) <xref:System.Boolean>, `Nothing` literal ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) e `null` (C#), e outros problemas semelhantes.</span><span class="sxs-lookup"><span data-stu-id="229f7-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="229f7-108">Conversão de operador de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="229f7-108">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|<span data-ttu-id="229f7-109">“A seção de semântica nula” neste tópico descreve as semânticas nula de comparação em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="229f7-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="229f7-110">Métodos de System. String</span><span class="sxs-lookup"><span data-stu-id="229f7-110">System.String Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|<span data-ttu-id="229f7-111">As “diferenças a seção .NET” neste tópico descrevem como um retorno de 0 de <xref:System.String.LastIndexOf%2A> pode significar qualquer pessoa que a cadeia de caracteres é nula ou que a posição encontrada é 0.</span><span class="sxs-lookup"><span data-stu-id="229f7-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="229f7-112">Calcular a soma dos valores em uma sequência numérica</span><span class="sxs-lookup"><span data-stu-id="229f7-112">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="229f7-113">Descreve como o <xref:System.Linq.Enumerable.Sum%2A> operador é avaliada como `null` (`Nothing` em [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) em vez de 0 para uma sequência que contém apenas valores nulos ou para uma sequência vazia.</span><span class="sxs-lookup"><span data-stu-id="229f7-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="229f7-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="229f7-114">See Also</span></span>  
 [<span data-ttu-id="229f7-115">Funções e tipos de dados</span><span class="sxs-lookup"><span data-stu-id="229f7-115">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
