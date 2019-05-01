---
title: Resolução de sobrecarga de função (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
ms.openlocfilehash: 0248fdd3f3ba6afb5c7edca740d9aad3ca74bd03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034171"
---
# <a name="function-overload-resolution-entity-sql"></a><span data-ttu-id="ff0fa-102">Resolução de sobrecarga de função (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ff0fa-102">Function Overload Resolution (Entity SQL)</span></span>
<span data-ttu-id="ff0fa-103">Este tópico descreve como as funções de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são resolvidas.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-103">This topic describes how [!INCLUDE[esql](../../../../../../includes/esql-md.md)] functions are resolved.</span></span>  
  
 <span data-ttu-id="ff0fa-104">Mais de uma função pode ser definida com o mesmo nome, como as funções tenham assinaturas exclusivos.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-104">More than one function can be defined with the same name, as long as the functions have unique signatures.</span></span>  
  
 <span data-ttu-id="ff0fa-105">Quando esse for o caso, os seguintes critérios devem ser aplicados para determinar que a função é referenciada por uma expressão fornecida.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-105">When this is the case, the following criteria must be applied to determine which function is referenced by a given expression.</span></span> <span data-ttu-id="ff0fa-106">Esses critérios são aplicados em ordem.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-106">These criteria are applied in sequence.</span></span> <span data-ttu-id="ff0fa-107">O primeiro critério que se aplica a uma única função é a função resolvida.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-107">The first criterion that applies only to a single function is the resolved function.</span></span>  
  
1. <span data-ttu-id="ff0fa-108">**Número do parâmetro**.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-108">**Parameter number**.</span></span> <span data-ttu-id="ff0fa-109">A função tem o mesmo número de parâmetros especificados na expressão.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-109">The function has the same number of parameters specified in the expression.</span></span>  
  
2. <span data-ttu-id="ff0fa-110">**Correspondência exata no tipo**.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-110">**Exact match on type**.</span></span> <span data-ttu-id="ff0fa-111">Cada tipo de argumento de função corresponde exatamente o tipo de parâmetro, ou é o literal nulo.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-111">Each argument type of the function exactly matches the parameter type, or is the null literal.</span></span>  
  
3. <span data-ttu-id="ff0fa-112">**1&gt;match on Subtype&lt;1**.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-112">**Match on subtype**.</span></span> <span data-ttu-id="ff0fa-113">Cada tipo de argumento corresponde exatamente de função ou subpropriedades é um tipo de parâmetro, ou o argumento é o literal nulo.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-113">Each argument type of the function exactly matches or is a sub-type of the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="ff0fa-114">Se várias funções diferem somente no número de conversões de tipo subpropriedades necessárias, a função com menos número de subpropriedades conversões de tipo é a função resolvida.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-114">In the event that several functions differ only in the number of sub-type conversions required, the function with the least number of sub-type conversions is the resolved function.</span></span>  
  
4. <span data-ttu-id="ff0fa-115">**1&gt;match on subtype or type Promotion&lt;1**.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-115">**Match on subtype or type promotion**.</span></span> <span data-ttu-id="ff0fa-116">Cada tipo de argumento corresponde exatamente de função, é um tipo de subpropriedades, ou pode ser elevado ao tipo de parâmetro, ou o argumento é o literal nulo.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-116">Each argument type of the function exactly matches, is a sub-type of, or can be promoted to the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="ff0fa-117">Além disso, se várias funções diferem somente no número de conversões e de promoções de subpropriedades tipo, a função com menos número de subpropriedades conversões de tipo e as promoções a função é resolvida.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-117">Again, in the event that several functions differ only in the number of sub-type conversions and promotions, the function with the least number of sub-type conversions and promotions is the resolved function.</span></span>  
  
 <span data-ttu-id="ff0fa-118">Se nenhum desses critérios resultam em uma única função que está sendo selecionada, a expressão de chamada de função é ambígua.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-118">If none of these criteria result in a single function being selected, the function invocation expression is ambiguous.</span></span>  
  
 <span data-ttu-id="ff0fa-119">Mesmo se uma única função pode ser extraída usando essas regras, os argumentos ainda podem não corresponder os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-119">Even if a single function can be extracted using these rules, the arguments still might not match the parameters.</span></span> <span data-ttu-id="ff0fa-120">Um erro é gerado nesse caso.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-120">An error is raised in this case.</span></span>  
  
 <span data-ttu-id="ff0fa-121">Para funções definidas pelo usuário, a definição de uma função in-line de consulta tem precedência mesmo quando uma função o definida existe com uma assinatura que é uma correspondência melhor para a função definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="ff0fa-121">For user-defined functions, the definition for an inline query function takes precedence even when a model-defined function exists with a signature that is a better match for the user-defined function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff0fa-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff0fa-122">See also</span></span>

- [<span data-ttu-id="ff0fa-123">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ff0fa-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="ff0fa-124">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ff0fa-124">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="ff0fa-125">Funções</span><span class="sxs-lookup"><span data-stu-id="ff0fa-125">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
