---
title: Interface ICorDebugGCReferenceEnum
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
ms.openlocfilehash: f01c27376191c3a2dddf56dae4b26c8b5193c73e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788650"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="86748-102">Interface ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="86748-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="86748-103">Fornece um enumerador para objetos que serão coletados do lixo.</span><span class="sxs-lookup"><span data-stu-id="86748-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="86748-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="86748-104">Methods</span></span>  
  
|<span data-ttu-id="86748-105">Método</span><span class="sxs-lookup"><span data-stu-id="86748-105">Method</span></span>|<span data-ttu-id="86748-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="86748-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="86748-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="86748-107">Next Method</span></span>](icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="86748-108">Obtém o número especificado de instâncias de [COR_GC_REFERENCE](cor-gc-reference-structure.md) que contêm informações sobre objetos que serão coletados como lixo.</span><span class="sxs-lookup"><span data-stu-id="86748-108">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86748-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="86748-109">Remarks</span></span>  
 <span data-ttu-id="86748-110">A interface `ICorDebugGCReferenceEnum` implementa a interface "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="86748-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="86748-111">Uma instância de `ICorDebugGCReferenceEnum` é populada com instâncias de [COR_GC_REFERENCE](cor-gc-reference-structure.md) chamando o método [ICorDebugProcess5:: EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="86748-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="86748-112">[COR_GC_REFERENCE](cor-gc-reference-structure.md) objetos podem ser enumerados chamando o método [ICorDebugGCReference:: Next](icordebuggcreferenceenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="86748-112">[COR_GC_REFERENCE](cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="86748-113">Os objetos [COR_GC_REFERENCE](cor-gc-reference-structure.md) na coleção preenchida por esse método representam três tipos de objetos:</span><span class="sxs-lookup"><span data-stu-id="86748-113">The [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
- <span data-ttu-id="86748-114">Objetos de todas as pilhas gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="86748-114">Objects from all managed stacks.</span></span> <span data-ttu-id="86748-115">Isso inclui referências dinâmicas em código gerenciado, bem como objetos criados pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="86748-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="86748-116">Objetos da tabela de identificadores.</span><span class="sxs-lookup"><span data-stu-id="86748-116">Objects from the handle table.</span></span> <span data-ttu-id="86748-117">Isso inclui referências fortes (`HNDTYPE_STRONG` e `HNDTYPE_REFCOUNT`) e variáveis estáticas em um módulo.</span><span class="sxs-lookup"><span data-stu-id="86748-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="86748-118">Objetos da fila do finalizador.</span><span class="sxs-lookup"><span data-stu-id="86748-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="86748-119">O finalizador enfileira objetos de raízes até que o finalizador tenha sido executado.</span><span class="sxs-lookup"><span data-stu-id="86748-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86748-120">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="86748-120">Requirements</span></span>  
 <span data-ttu-id="86748-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86748-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86748-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86748-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86748-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86748-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86748-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86748-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86748-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="86748-125">See also</span></span>

- [<span data-ttu-id="86748-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="86748-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
