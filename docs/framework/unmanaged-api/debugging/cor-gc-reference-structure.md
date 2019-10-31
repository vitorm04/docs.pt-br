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
ms.openlocfilehash: 635cb0c003889beb2f78e8413189cbfc4b064175
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099138"
---
# <a name="cor_gc_reference-structure"></a><span data-ttu-id="69725-102">Estrutura COR_GC_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="69725-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="69725-103">Contém informações sobre um objeto que será coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="69725-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69725-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69725-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="69725-105">Membros</span><span class="sxs-lookup"><span data-stu-id="69725-105">Members</span></span>  
  
|<span data-ttu-id="69725-106">Membro</span><span class="sxs-lookup"><span data-stu-id="69725-106">Member</span></span>|<span data-ttu-id="69725-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="69725-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="69725-108">Um ponteiro para o domínio do aplicativo ao qual o identificador ou objeto pertence.</span><span class="sxs-lookup"><span data-stu-id="69725-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="69725-109">Seu valor pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="69725-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="69725-110">Uma interface ICorDebugValue ou ICorDebugReferenceValue que corresponde ao objeto a ser coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="69725-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="69725-111">Um valor de enumeração [CorGCReferenceType](corgcreferencetype-enumeration.md) que indica de onde veio a raiz.</span><span class="sxs-lookup"><span data-stu-id="69725-111">A [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="69725-112">Para obter mais informações, consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="69725-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="69725-113">Dados adicionais sobre o objeto a ser coletado pelo lixo.</span><span class="sxs-lookup"><span data-stu-id="69725-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="69725-114">Essas informações dependem da origem do objeto, conforme indicado pelo campo `type`.</span><span class="sxs-lookup"><span data-stu-id="69725-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="69725-115">Para obter mais informações, consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="69725-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69725-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="69725-116">Remarks</span></span>  
 <span data-ttu-id="69725-117">O campo `type` é um valor de enumeração [CorGCReferenceType](corgcreferencetype-enumeration.md) que indica de onde veio a referência.</span><span class="sxs-lookup"><span data-stu-id="69725-117">The `type` field is a [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="69725-118">Um determinado valor de `COR_GC_REFERENCE` pode refletir qualquer um dos seguintes tipos de objetos gerenciados:</span><span class="sxs-lookup"><span data-stu-id="69725-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="69725-119">Objetos de todas as pilhas gerenciadas (`CorGCReferenceType.CorReferenceStack`).</span><span class="sxs-lookup"><span data-stu-id="69725-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="69725-120">Isso inclui referências dinâmicas em código gerenciado, bem como objetos criados pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="69725-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="69725-121">Objetos da tabela de identificadores (`CorGCReferenceType.CorHandle*`).</span><span class="sxs-lookup"><span data-stu-id="69725-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="69725-122">Isso inclui referências fortes (`HNDTYPE_STRONG` e `HNDTYPE_REFCOUNT`) e variáveis estáticas em um módulo.</span><span class="sxs-lookup"><span data-stu-id="69725-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="69725-123">Objetos da fila do finalizador (`CorGCReferenceType.CorReferenceFinalizer`).</span><span class="sxs-lookup"><span data-stu-id="69725-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="69725-124">O finalizador enfileira objetos de raízes até que o finalizador tenha sido executado.</span><span class="sxs-lookup"><span data-stu-id="69725-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="69725-125">O campo `extraData` contém dados extras, dependendo da origem (ou tipo) da referência.</span><span class="sxs-lookup"><span data-stu-id="69725-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="69725-126">Os possíveis valores são:</span><span class="sxs-lookup"><span data-stu-id="69725-126">Possible values are:</span></span>  
  
- <span data-ttu-id="69725-127">`DependentSource`</span><span class="sxs-lookup"><span data-stu-id="69725-127">`DependentSource`.</span></span> <span data-ttu-id="69725-128">Se o `type` for `CorGCREferenceType.CorHandleStrongDependent`, esse campo será o objeto que, se estiver ativo, terá como raiz o objeto a ser coletado pelo lixo em `COR_GC_REFERENCE.Location`.</span><span class="sxs-lookup"><span data-stu-id="69725-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="69725-129">`RefCount`</span><span class="sxs-lookup"><span data-stu-id="69725-129">`RefCount`.</span></span> <span data-ttu-id="69725-130">Se o `type` for `CorGCREferenceType.CorHandleStrongRefCount`, esse campo será a contagem de referência do identificador.</span><span class="sxs-lookup"><span data-stu-id="69725-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="69725-131">`Size`</span><span class="sxs-lookup"><span data-stu-id="69725-131">`Size`.</span></span> <span data-ttu-id="69725-132">Se o `type` for `CorGCREferenceType.CorHandleStrongSizedByref`, esse campo será o último tamanho da árvore de objetos para a qual o coletor de lixo calculou as raízes do objeto.</span><span class="sxs-lookup"><span data-stu-id="69725-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="69725-133">Observe que esse cálculo não está necessariamente atualizado.</span><span class="sxs-lookup"><span data-stu-id="69725-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69725-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="69725-134">Requirements</span></span>  
 <span data-ttu-id="69725-135">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69725-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69725-136">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69725-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69725-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69725-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69725-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69725-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69725-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69725-139">See also</span></span>

- [<span data-ttu-id="69725-140">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="69725-140">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="69725-141">Depuração</span><span class="sxs-lookup"><span data-stu-id="69725-141">Debugging</span></span>](index.md)
