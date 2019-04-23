---
title: Estrutura COR_GC_REFERENCE
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1e31e95473136bf7e7c196eacc278fa8a1caab2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093651"
---
# <a name="corgcreference-structure"></a><span data-ttu-id="d6b4e-102">Estrutura COR_GC_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="d6b4e-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="d6b4e-103">Contém informações sobre um objeto que será coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6b4e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6b4e-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="d6b4e-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d6b4e-105">Members</span></span>  
  
|<span data-ttu-id="d6b4e-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d6b4e-106">Member</span></span>|<span data-ttu-id="d6b4e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6b4e-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="d6b4e-108">Um ponteiro para o domínio do aplicativo ao qual pertence o identificador ou um objeto.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="d6b4e-109">Seu valor pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="d6b4e-110">Um ICorDebugValue ou uma interface ICorDebugReferenceValue que corresponde ao objeto seja coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="d6b4e-111">Um [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) valor de enumeração que indica de onde veio a raiz.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="d6b4e-112">Para obter mais informações, consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="d6b4e-113">Dados adicionais sobre o objeto a ser coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="d6b4e-114">Essas informações dependem da origem do objeto, conforme indicado pelo `type` campo.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="d6b4e-115">Para obter mais informações, consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6b4e-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6b4e-116">Remarks</span></span>  
 <span data-ttu-id="d6b4e-117">O `type` campo é um [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) valor de enumeração que indica de onde veio a referência.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-117">The `type` field is a [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="d6b4e-118">Um determinado `COR_GC_REFERENCE` valor pode refletir qualquer um dos seguintes tipos de objetos gerenciados:</span><span class="sxs-lookup"><span data-stu-id="d6b4e-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
-   <span data-ttu-id="d6b4e-119">Objetos de todas as pilhas gerenciadas (`CorGCReferenceType.CorReferenceStack`).</span><span class="sxs-lookup"><span data-stu-id="d6b4e-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="d6b4e-120">Isso inclui referências ao vivo em código gerenciado, bem como objetos criados pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
-   <span data-ttu-id="d6b4e-121">Objetos da tabela de identificador (`CorGCReferenceType.CorHandle*`).</span><span class="sxs-lookup"><span data-stu-id="d6b4e-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="d6b4e-122">Isso inclui referências fortes (`HNDTYPE_STRONG` e `HNDTYPE_REFCOUNT`) e as variáveis estáticas em um módulo.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
-   <span data-ttu-id="d6b4e-123">Objetos da fila do finalizador (`CorGCReferenceType.CorReferenceFinalizer`).</span><span class="sxs-lookup"><span data-stu-id="d6b4e-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="d6b4e-124">A fila de finalizadores raízes objetos até que o finalizador foi executado.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="d6b4e-125">O `extraData` campo contém dados extras, dependendo do código-fonte (ou tipo) da referência.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="d6b4e-126">Os possíveis valores são:</span><span class="sxs-lookup"><span data-stu-id="d6b4e-126">Possible values are:</span></span>  
  
-   <span data-ttu-id="d6b4e-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-127">`DependentSource`.</span></span> <span data-ttu-id="d6b4e-128">Se o `type` está `CorGCREferenceType.CorHandleStrongDependent`, esse campo é o objeto que, se estiver ativo, raízes no objeto a ser coletado como lixo no `COR_GC_REFERENCE.Location`.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
-   <span data-ttu-id="d6b4e-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-129">`RefCount`.</span></span> <span data-ttu-id="d6b4e-130">Se o `type` é `CorGCREferenceType.CorHandleStrongRefCount`, esse campo é a contagem de referência do identificador.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
-   <span data-ttu-id="d6b4e-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-131">`Size`.</span></span> <span data-ttu-id="d6b4e-132">Se o `type` é `CorGCREferenceType.CorHandleStrongSizedByref`, esse campo é o último tamanho da árvore de objetos para o qual o coletor de lixo calculada as raízes de objeto.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="d6b4e-133">Observe que esse cálculo não é necessariamente atualizado.</span><span class="sxs-lookup"><span data-stu-id="d6b4e-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6b4e-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6b4e-134">Requirements</span></span>  
 <span data-ttu-id="d6b4e-135">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6b4e-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6b4e-136">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6b4e-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6b4e-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6b4e-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6b4e-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6b4e-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6b4e-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6b4e-139">See also</span></span>

- [<span data-ttu-id="d6b4e-140">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="d6b4e-140">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="d6b4e-141">Depuração</span><span class="sxs-lookup"><span data-stu-id="d6b4e-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
