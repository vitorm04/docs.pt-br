---
title: Método IMetaDataEmit::MergeEnd
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
ms.openlocfilehash: feb81b86190f953b50f43f244f4e58a0a482f86e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003913"
---
# <a name="imetadataemitmergeend-method"></a><span data-ttu-id="76cea-102">Método IMetaDataEmit::MergeEnd</span><span class="sxs-lookup"><span data-stu-id="76cea-102">IMetaDataEmit::MergeEnd Method</span></span>

<span data-ttu-id="76cea-103">Mescla no escopo atual todos os escopos de metadados especificados por uma ou mais chamadas anteriores para [IMetaDataEmit:: Merge](imetadataemit-merge-method.md).</span><span class="sxs-lookup"><span data-stu-id="76cea-103">Merges into the current scope all the metadata scopes specified by one or more prior calls to [IMetaDataEmit::Merge](imetadataemit-merge-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="76cea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76cea-104">Syntax</span></span>

```cppcpp
HRESULT MergeEnd ();
```

## <a name="parameters"></a><span data-ttu-id="76cea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="76cea-105">Parameters</span></span>

<span data-ttu-id="76cea-106">Esse método não usa parâmetros.</span><span class="sxs-lookup"><span data-stu-id="76cea-106">This method takes no parameters.</span></span>

## <a name="remarks"></a><span data-ttu-id="76cea-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="76cea-107">Remarks</span></span>

<span data-ttu-id="76cea-108">Essa rotina dispara a mesclagem real de metadados, de todos os escopos de importação especificados por chamadas anteriores para `IMetaDataEmit::Merge` , no escopo de saída atual.</span><span class="sxs-lookup"><span data-stu-id="76cea-108">This routine triggers the actual merge of metadata, of all import scopes specified by preceding calls to `IMetaDataEmit::Merge`, into the current output scope.</span></span>

<span data-ttu-id="76cea-109">As seguintes condições especiais se aplicam à mesclagem:</span><span class="sxs-lookup"><span data-stu-id="76cea-109">The following special conditions apply to the merge:</span></span>

- <span data-ttu-id="76cea-110">Um MVID (identificador de versão do módulo) nunca é importado, pois é exclusivo para os metadados no escopo de importação.</span><span class="sxs-lookup"><span data-stu-id="76cea-110">A module version identifier (MVID) is never imported, because it is unique to the metadata in the import scope.</span></span>

- <span data-ttu-id="76cea-111">Nenhuma propriedade existente em todo o módulo é substituída.</span><span class="sxs-lookup"><span data-stu-id="76cea-111">No existing module-wide properties are overwritten.</span></span>

  <span data-ttu-id="76cea-112">Se as propriedades do módulo já foram definidas para o escopo atual, nenhuma Propriedade do módulo será importada.</span><span class="sxs-lookup"><span data-stu-id="76cea-112">If module properties were already set for the current scope, no module properties are imported.</span></span> <span data-ttu-id="76cea-113">No entanto, se as propriedades do módulo não tiverem sido definidas no escopo atual, elas serão importadas apenas uma vez, quando forem encontradas.</span><span class="sxs-lookup"><span data-stu-id="76cea-113">However, if module properties have not been set in the current scope, they are imported only once, when they are first encountered.</span></span> <span data-ttu-id="76cea-114">Se essas propriedades de módulo forem encontradas novamente, elas serão duplicadas.</span><span class="sxs-lookup"><span data-stu-id="76cea-114">If those module properties are encountered again, they are duplicates.</span></span> <span data-ttu-id="76cea-115">Se os valores de todas as propriedades do módulo (exceto MVID) forem comparados e nenhuma duplicata for encontrada, um erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="76cea-115">If the values of all module properties (except MVID) are compared and no duplicates are found, an error is raised.</span></span>

- <span data-ttu-id="76cea-116">Para definições de tipo ( `TypeDef` ), nenhuma duplicata é mesclada no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="76cea-116">For type definitions (`TypeDef`), no duplicates are merged into the current scope.</span></span> <span data-ttu-id="76cea-117">`TypeDef`os objetos são verificados em busca de duplicatas em relação a cada número de versão GUID *de nome de objeto totalmente qualificado*  +  *GUID*  +  *version number*.</span><span class="sxs-lookup"><span data-stu-id="76cea-117">`TypeDef` objects are checked for duplicates against each *fully-qualified object name* + *GUID* + *version number*.</span></span> <span data-ttu-id="76cea-118">Se houver uma correspondência no nome ou GUID, e qualquer um dos outros dois elementos for diferente, um erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="76cea-118">If there is a match on either name or GUID, and any of the other two elements is different, an error is raised.</span></span> <span data-ttu-id="76cea-119">Caso contrário, se todos os três itens corresponderem, `MergeEnd` uma verificação de cursor garantirá que as entradas sejam, de fato, duplicadas; caso contrário, um erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="76cea-119">Otherwise, if all three items match, `MergeEnd` does a cursory check to ensure the entries are indeed duplicates; if not, an error is raised.</span></span> <span data-ttu-id="76cea-120">Esta verificação de cursor procura:</span><span class="sxs-lookup"><span data-stu-id="76cea-120">This cursory check looks for:</span></span>

  - <span data-ttu-id="76cea-121">As mesmas declarações de membro, que ocorrem na mesma ordem.</span><span class="sxs-lookup"><span data-stu-id="76cea-121">The same member declarations, occurring in the same order.</span></span> <span data-ttu-id="76cea-122">Os membros que são sinalizados como `mdPrivateScope` (consulte a enumeração [CorMethodAttr](cormethodattr-enumeration.md) ) não são incluídos nessa verificação; eles são mesclados especialmente.</span><span class="sxs-lookup"><span data-stu-id="76cea-122">Members that are flagged as `mdPrivateScope` (see the [CorMethodAttr](cormethodattr-enumeration.md) enumeration) are not included in this check; they are merged specially.</span></span>

  - <span data-ttu-id="76cea-123">O mesmo layout de classe.</span><span class="sxs-lookup"><span data-stu-id="76cea-123">The same class layout.</span></span>

  <span data-ttu-id="76cea-124">Isso significa que um `TypeDef` objeto sempre deve ser totalmente e consistentemente definido em cada escopo de metadados no qual ele é declarado; se suas implementações de membro (para uma classe) forem distribuídas entre várias unidades de compilação, a definição completa será considerada como presente em todos os escopos e não incremental para cada escopo.</span><span class="sxs-lookup"><span data-stu-id="76cea-124">This means that a `TypeDef` object must always be fully and consistently defined in every metadata scope in which it is declared; if its member implementations (for a class) are spread across multiple compilation units, the full definition is assumed to be present in every scope and not incremental to each scope.</span></span> <span data-ttu-id="76cea-125">Por exemplo, se os nomes de parâmetros forem relevantes para o contrato, eles deverão ser emitidos da mesma maneira em todos os escopos; Se não forem relevantes, eles não deverão ser emitidos em metadados.</span><span class="sxs-lookup"><span data-stu-id="76cea-125">For example, if parameter names are relevant to the contract, they must be emitted the same way into every scope; if they are not relevant, they should not be emitted into metadata.</span></span>

  <span data-ttu-id="76cea-126">A exceção é que um `TypeDef` objeto pode ter membros incrementais sinalizados como `mdPrivateScope` .</span><span class="sxs-lookup"><span data-stu-id="76cea-126">The exception is that a `TypeDef` object can have incremental members flagged as `mdPrivateScope`.</span></span> <span data-ttu-id="76cea-127">Ao encontrar esses, os `MergeEnd` adiciona incrementalmente ao escopo atual sem considerar duplicatas.</span><span class="sxs-lookup"><span data-stu-id="76cea-127">On encountering these, `MergeEnd` incrementally adds them to the current scope without regard for duplicates.</span></span> <span data-ttu-id="76cea-128">Como o compilador compreende o escopo privado, o compilador deve ser responsável por impor regras.</span><span class="sxs-lookup"><span data-stu-id="76cea-128">Because the compiler understands the private scope, the compiler must be responsible for enforcing rules.</span></span>

- <span data-ttu-id="76cea-129">Os endereços virtuais relativos (RVAs) não são importados ou mesclados; Espera-se que o compilador emita novamente essas informações.</span><span class="sxs-lookup"><span data-stu-id="76cea-129">Relative virtual addresses (RVAs) are not imported or merged; the compiler is expected to re-emit this information.</span></span>

- <span data-ttu-id="76cea-130">Os atributos personalizados são mesclados somente quando o item ao qual eles são anexados é mesclado.</span><span class="sxs-lookup"><span data-stu-id="76cea-130">Custom attributes are merged only when the item to which they are attached is merged.</span></span> <span data-ttu-id="76cea-131">Por exemplo, os atributos personalizados associados a uma classe são mesclados quando a classe é encontrada pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="76cea-131">For example, custom attributes associated with a class are merged when the class is first encountered.</span></span> <span data-ttu-id="76cea-132">Se os atributos personalizados estiverem associados a um `TypeDef` ou `MemberDef` que seja específico para a unidade de compilação (como o carimbo de data/hora de uma compilação de membro), eles não serão mesclados e o compilador deve remover ou atualizar esses metadados.</span><span class="sxs-lookup"><span data-stu-id="76cea-132">If custom attributes are associated with a `TypeDef` or `MemberDef` that is specific to the compilation unit (such as the time stamp of a member compile), they are not merged and it is up to the compiler to remove or update such metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="76cea-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="76cea-133">Requirements</span></span>

<span data-ttu-id="76cea-134">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76cea-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="76cea-135">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="76cea-135">**Header:** Cor.h</span></span>

<span data-ttu-id="76cea-136">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="76cea-136">**Library:** Used as a resource in MSCorEE.dll</span></span>

<span data-ttu-id="76cea-137">**.NET Framework versões:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76cea-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="76cea-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="76cea-138">See also</span></span>

- [<span data-ttu-id="76cea-139">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="76cea-139">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="76cea-140">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="76cea-140">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
