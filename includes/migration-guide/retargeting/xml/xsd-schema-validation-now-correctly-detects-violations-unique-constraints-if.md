---
ms.openlocfilehash: 349854b0dec5a585990b9c5e7c0b575df5bf70f3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615600"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a><span data-ttu-id="efe84-101">A validação do Esquema XSD agora detecta corretamente as violações de restrições exclusivas se chaves compostas forem usadas e uma chave estiver vazia</span><span class="sxs-lookup"><span data-stu-id="efe84-101">XSD Schema validation now correctly detects violations of unique constraints if compound keys are used and one key is empty</span></span>

#### <a name="details"></a><span data-ttu-id="efe84-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="efe84-102">Details</span></span>

<span data-ttu-id="efe84-103">As versões do .NET Framework anteriores a 4.6 tinham um bug que fazia com que a validação de XSD não detectasse restrições exclusivas em chaves compostas se uma das chaves estivesse vazia.</span><span class="sxs-lookup"><span data-stu-id="efe84-103">Versions of the .NET Framework prior to 4.6 had a bug that caused XSD validation to not detect unique constraints on compound keys if one of the keys was empty.</span></span> <span data-ttu-id="efe84-104">No .NET Framework 4.6, esse problema foi corrigido.</span><span class="sxs-lookup"><span data-stu-id="efe84-104">In the .NET Framework 4.6, this issue is corrected.</span></span> <span data-ttu-id="efe84-105">Isso resultará na validação mais correta, mas também pode resultar na não validação de algum XML que anteriormente seria validado.</span><span class="sxs-lookup"><span data-stu-id="efe84-105">This will result in more correct validation, but it may also result in some XML not validating which previously would have.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="efe84-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="efe84-106">Suggestion</span></span>

<span data-ttu-id="efe84-107">Se for necessária uma validação menos rigorosa do .NET Framework 4.0, o aplicativo de validação poderá ser destinado à versão 4.5 (ou anterior) do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="efe84-107">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.5 (or earlier) of the .NET Framework.</span></span> <span data-ttu-id="efe84-108">No entanto, ao redirecionar para o .NET Framework 4.6, será necessário fazer uma revisão de código para garantir que não seja esperado que chaves compostas duplicadas (conforme é descrito na descrição desse problema) sejam validadas.</span><span class="sxs-lookup"><span data-stu-id="efe84-108">When retargeting to .NET Framework 4.6, however, code review should be done to be sure that duplicate compound keys (as described in this issue's description) are not expected to validate.</span></span>

| <span data-ttu-id="efe84-109">Name</span><span class="sxs-lookup"><span data-stu-id="efe84-109">Name</span></span>    | <span data-ttu-id="efe84-110">Valor</span><span class="sxs-lookup"><span data-stu-id="efe84-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="efe84-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="efe84-111">Scope</span></span>   | <span data-ttu-id="efe84-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="efe84-112">Edge</span></span>        |
| <span data-ttu-id="efe84-113">Versão</span><span class="sxs-lookup"><span data-stu-id="efe84-113">Version</span></span> | <span data-ttu-id="efe84-114">4.6</span><span class="sxs-lookup"><span data-stu-id="efe84-114">4.6</span></span>         |
| <span data-ttu-id="efe84-115">Type</span><span class="sxs-lookup"><span data-stu-id="efe84-115">Type</span></span>    | <span data-ttu-id="efe84-116">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="efe84-116">Retargeting</span></span> |
