---
title: Interface ICorDebugProcess5
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a105ca8838820b62e81dae4c0149734339bed7a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620208"
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="a9072-102">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="a9072-102">ICorDebugProcess5 Interface</span></span>
<span data-ttu-id="a9072-103">Estende a interface ICorDebugProcess para suportar o acesso para o heap gerenciado, para fornecer informações sobre a coleta de lixo de objetos gerenciados, e determinar se um depurador carrega imagens do cache de imagem nativo local do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a9072-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a9072-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a9072-104">Methods</span></span>  
  
|<span data-ttu-id="a9072-105">Método</span><span class="sxs-lookup"><span data-stu-id="a9072-105">Method</span></span>|<span data-ttu-id="a9072-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9072-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a9072-107">Método EnableNGenPolicy</span><span class="sxs-lookup"><span data-stu-id="a9072-107">EnableNGenPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="a9072-108">Define um valor que determina como um aplicativo carrega as imagens nativas durante a execução em um depurador gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a9072-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="a9072-109">Método EnumerateGCReferences</span><span class="sxs-lookup"><span data-stu-id="a9072-109">EnumerateGCReferences Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="a9072-110">Obtém um enumerador para todos os objetos que precisam estar em um processo de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a9072-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="a9072-111">Método EnumerateHandles</span><span class="sxs-lookup"><span data-stu-id="a9072-111">EnumerateHandles Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="a9072-112">Obtém um enumerador para os identificadores de objeto em um processo.</span><span class="sxs-lookup"><span data-stu-id="a9072-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="a9072-113">Método EnumerateHeap</span><span class="sxs-lookup"><span data-stu-id="a9072-113">EnumerateHeap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="a9072-114">Obtém um enumerador para objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a9072-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="a9072-115">Método EnumerateHeapRegions</span><span class="sxs-lookup"><span data-stu-id="a9072-115">EnumerateHeapRegions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="a9072-116">Obtém um enumerador para regiões do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a9072-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="a9072-117">Método GetArrayLayout</span><span class="sxs-lookup"><span data-stu-id="a9072-117">GetArrayLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="a9072-118">Obtém informações sobre o layout de uma matriz na memória.</span><span class="sxs-lookup"><span data-stu-id="a9072-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="a9072-119">Método GetGCHeapInformation</span><span class="sxs-lookup"><span data-stu-id="a9072-119">GetGCHeapInformation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="a9072-120">Obtém um ponteiro para um [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) estrutura que contém informações sobre os objetos que devem ser coletado como lixo no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a9072-120">Gets a pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="a9072-121">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="a9072-121">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|<span data-ttu-id="a9072-122">Obtém um ponteiro para um objeto no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a9072-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="a9072-123">Método GetTypeFields</span><span class="sxs-lookup"><span data-stu-id="a9072-123">GetTypeFields Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="a9072-124">Obtém um ponteiro para uma matriz que contém informações de campo para um tipo com base em seu identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="a9072-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="a9072-125">Método GetTypeForTypeID</span><span class="sxs-lookup"><span data-stu-id="a9072-125">GetTypeForTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="a9072-126">Obtém um objeto do tipo que fornece informações sobre um objeto com base em seus identificadores de tipo.</span><span class="sxs-lookup"><span data-stu-id="a9072-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="a9072-127">Método GetTypeID</span><span class="sxs-lookup"><span data-stu-id="a9072-127">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="a9072-128">Obtém o identificador de tipo para o objeto em um endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="a9072-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="a9072-129">Método GetTypeLayout</span><span class="sxs-lookup"><span data-stu-id="a9072-129">GetTypeLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="a9072-130">Obtém informações sobre o layout de um objeto na memória com base em seu identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="a9072-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9072-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="a9072-131">Remarks</span></span>  
 <span data-ttu-id="a9072-132">Essa interface estende logicamente a ICorDebugProcess, ICorDebugProcess2, e [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfaces.</span><span class="sxs-lookup"><span data-stu-id="a9072-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9072-133">Essa interface não dá suporte a ser chamada remotamente, de outro computador ou de outro processo.</span><span class="sxs-lookup"><span data-stu-id="a9072-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9072-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a9072-134">Requirements</span></span>  
 <span data-ttu-id="a9072-135">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9072-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9072-136">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9072-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9072-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9072-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9072-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9072-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9072-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9072-139">See also</span></span>
- [<span data-ttu-id="a9072-140">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a9072-140">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a9072-141">Depuração</span><span class="sxs-lookup"><span data-stu-id="a9072-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
