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
ms.openlocfilehash: 1953a3e0492e4cfcdaea761b68ea22cf5a4a8ed7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205528"
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="9a975-102">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="9a975-102">ICorDebugProcess5 Interface</span></span>
<span data-ttu-id="9a975-103">Estende a interface ICorDebugProcess para dar suporte ao acesso ao heap gerenciado, para fornecer informações sobre a coleta de lixo de objetos gerenciados e para determinar se um depurador carrega imagens do cache de imagem nativa local do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9a975-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9a975-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9a975-104">Methods</span></span>  
  
|<span data-ttu-id="9a975-105">Método</span><span class="sxs-lookup"><span data-stu-id="9a975-105">Method</span></span>|<span data-ttu-id="9a975-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a975-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9a975-107">Método EnableNGenPolicy</span><span class="sxs-lookup"><span data-stu-id="9a975-107">EnableNGenPolicy Method</span></span>](icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="9a975-108">Define um valor que determina como um aplicativo carrega imagens nativas durante a execução em um depurador gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9a975-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="9a975-109">Método EnumerateGCReferences</span><span class="sxs-lookup"><span data-stu-id="9a975-109">EnumerateGCReferences Method</span></span>](icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="9a975-110">Obtém um enumerador para todos os objetos que devem ser coletados pelo lixo em um processo.</span><span class="sxs-lookup"><span data-stu-id="9a975-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="9a975-111">Método EnumerateHandles</span><span class="sxs-lookup"><span data-stu-id="9a975-111">EnumerateHandles Method</span></span>](icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="9a975-112">Obtém um enumerador para identificadores de objeto em um processo.</span><span class="sxs-lookup"><span data-stu-id="9a975-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="9a975-113">Método EnumerateHeap</span><span class="sxs-lookup"><span data-stu-id="9a975-113">EnumerateHeap Method</span></span>](icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="9a975-114">Obtém um enumerador para objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9a975-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="9a975-115">Método EnumerateHeapRegions</span><span class="sxs-lookup"><span data-stu-id="9a975-115">EnumerateHeapRegions Method</span></span>](icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="9a975-116">Obtém um enumerador para regiões do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9a975-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="9a975-117">Método GetArrayLayout</span><span class="sxs-lookup"><span data-stu-id="9a975-117">GetArrayLayout Method</span></span>](icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="9a975-118">Obtém informações sobre o layout de uma matriz na memória.</span><span class="sxs-lookup"><span data-stu-id="9a975-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="9a975-119">Método GetGCHeapInformation</span><span class="sxs-lookup"><span data-stu-id="9a975-119">GetGCHeapInformation Method</span></span>](icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="9a975-120">Obtém um ponteiro para uma estrutura de [COR_HEAPINFO](cor-heapinfo-structure.md) que contém informações sobre objetos que devem ser coletados pelo lixo no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9a975-120">Gets a pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="9a975-121">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="9a975-121">GetObject Method</span></span>](icordebugprocess5-getobject-method.md)|<span data-ttu-id="9a975-122">Obtém um ponteiro para um objeto no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9a975-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="9a975-123">Método GetTypeFields</span><span class="sxs-lookup"><span data-stu-id="9a975-123">GetTypeFields Method</span></span>](icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="9a975-124">Obtém um ponteiro para uma matriz que contém informações de campo para um tipo com base em seu identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="9a975-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="9a975-125">Método GetTypeForTypeID</span><span class="sxs-lookup"><span data-stu-id="9a975-125">GetTypeForTypeID Method</span></span>](icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="9a975-126">Obtém um objeto de tipo que fornece informações sobre um objeto com base em seus identificadores de tipo.</span><span class="sxs-lookup"><span data-stu-id="9a975-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="9a975-127">Método GetTypeID</span><span class="sxs-lookup"><span data-stu-id="9a975-127">GetTypeID Method</span></span>](icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="9a975-128">Obtém o identificador de tipo para o objeto em um endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="9a975-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="9a975-129">Método GetTypeLayout</span><span class="sxs-lookup"><span data-stu-id="9a975-129">GetTypeLayout Method</span></span>](icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="9a975-130">Obtém informações sobre o layout de um objeto na memória com base em seu identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="9a975-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a975-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a975-131">Remarks</span></span>  
 <span data-ttu-id="9a975-132">Essa interface estende logicamente as interfaces ICorDebugProcess, ICorDebugProcess2 e [ICorDebugProcess3](icordebugprocess3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9a975-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a975-133">Esta interface não dá suporte a chamadas remotas de outro computador ou de outro processo.</span><span class="sxs-lookup"><span data-stu-id="9a975-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a975-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9a975-134">Requirements</span></span>  
 <span data-ttu-id="9a975-135">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a975-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a975-136">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a975-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a975-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a975-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a975-138">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a975-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a975-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="9a975-139">See also</span></span>

- [<span data-ttu-id="9a975-140">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9a975-140">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9a975-141">Depuração</span><span class="sxs-lookup"><span data-stu-id="9a975-141">Debugging</span></span>](index.md)
