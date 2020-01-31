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
ms.openlocfilehash: 263124db75abdc058d26ffb606a13fc711aed8bf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792295"
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="ea1b6-102">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="ea1b6-102">ICorDebugProcess5 Interface</span></span>
<span data-ttu-id="ea1b6-103">Estende a interface ICorDebugProcess para dar suporte ao acesso ao heap gerenciado, para fornecer informações sobre a coleta de lixo de objetos gerenciados e para determinar se um depurador carrega imagens do cache de imagem nativa local do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea1b6-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ea1b6-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ea1b6-104">Methods</span></span>  
  
|<span data-ttu-id="ea1b6-105">Método</span><span class="sxs-lookup"><span data-stu-id="ea1b6-105">Method</span></span>|<span data-ttu-id="ea1b6-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea1b6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ea1b6-107">Método EnableNGenPolicy</span><span class="sxs-lookup"><span data-stu-id="ea1b6-107">EnableNGenPolicy Method</span></span>](icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="ea1b6-108">Define um valor que determina como um aplicativo carrega imagens nativas durante a execução em um depurador gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ea1b6-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="ea1b6-109">Método EnumerateGCReferences</span><span class="sxs-lookup"><span data-stu-id="ea1b6-109">EnumerateGCReferences Method</span></span>](icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="ea1b6-110">Obtém um enumerador para todos os objetos que devem ser coletados pelo lixo em um processo.</span><span class="sxs-lookup"><span data-stu-id="ea1b6-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="ea1b6-111">Método EnumerateHandles</span><span class="sxs-lookup"><span data-stu-id="ea1b6-111">EnumerateHandles Method</span></span>](icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="ea1b6-112">Obtém um enumerador para identificadores de objeto em um processo.</span><span class="sxs-lookup"><span data-stu-id="ea1b6-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="ea1b6-113">Método EnumerateHeap</span><span class="sxs-lookup"><span data-stu-id="ea1b6-113">EnumerateHeap Method</span></span>](icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="ea1b6-114">Obtém um enumerador para objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ea1b6-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="ea1b6-115">Método EnumerateHeapRegions</span><span class="sxs-lookup"><span data-stu-id="ea1b6-115">EnumerateHeapRegions Method</span></span>](icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="ea1b6-116">Obtém um enumerador para regiões do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ea1b6-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="ea1b6-117">Método GetArrayLayout</span><span class="sxs-lookup"><span data-stu-id="ea1b6-117">GetArrayLayout Method</span></span>](icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="ea1b6-118">Obtém informações sobre o layout de uma matriz na memória.</span><span class="sxs-lookup"><span data-stu-id="ea1b6-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="ea1b6-119">Método GetGCHeapInformation</span><span class="sxs-lookup"><span data-stu-id="ea1b6-119">GetGCHeapInformation Method</span></span>](icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="ea1b6-120">Obtém um ponteiro para uma estrutura de [COR_HEAPINFO](cor-heapinfo-structure.md) que contém informações sobre objetos que devem ser coletados pelo lixo no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ea1b6-120">Gets a pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="ea1b6-121">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="ea1b6-121">GetObject Method</span></span>](icordebugprocess5-getobject-method.md)|<span data-ttu-id="ea1b6-122">Obtém um ponteiro para um objeto no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ea1b6-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="ea1b6-123">Método GetTypeFields</span><span class="sxs-lookup"><span data-stu-id="ea1b6-123">GetTypeFields Method</span></span>](icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="ea1b6-124">Obtém um ponteiro para uma matriz que contém informações de campo para um tipo com base em seu identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="ea1b6-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="ea1b6-125">Método GetTypeForTypeID</span><span class="sxs-lookup"><span data-stu-id="ea1b6-125">GetTypeForTypeID Method</span></span>](icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="ea1b6-126">Obtém um objeto de tipo que fornece informações sobre um objeto com base em seus identificadores de tipo.</span><span class="sxs-lookup"><span data-stu-id="ea1b6-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="ea1b6-127">Método GetTypeID</span><span class="sxs-lookup"><span data-stu-id="ea1b6-127">GetTypeID Method</span></span>](icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="ea1b6-128">Obtém o identificador de tipo para o objeto em um endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="ea1b6-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="ea1b6-129">Método GetTypeLayout</span><span class="sxs-lookup"><span data-stu-id="ea1b6-129">GetTypeLayout Method</span></span>](icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="ea1b6-130">Obtém informações sobre o layout de um objeto na memória com base em seu identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="ea1b6-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea1b6-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="ea1b6-131">Remarks</span></span>  
 <span data-ttu-id="ea1b6-132">Essa interface estende logicamente as interfaces ICorDebugProcess, ICorDebugProcess2 e [ICorDebugProcess3](icordebugprocess3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ea1b6-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea1b6-133">Esta interface não dá suporte a chamadas remotas de outro computador ou de outro processo.</span><span class="sxs-lookup"><span data-stu-id="ea1b6-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea1b6-134">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ea1b6-134">Requirements</span></span>  
 <span data-ttu-id="ea1b6-135">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea1b6-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea1b6-136">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea1b6-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea1b6-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea1b6-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea1b6-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea1b6-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea1b6-139">Veja também</span><span class="sxs-lookup"><span data-stu-id="ea1b6-139">See also</span></span>

- [<span data-ttu-id="ea1b6-140">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ea1b6-140">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ea1b6-141">Depuração</span><span class="sxs-lookup"><span data-stu-id="ea1b6-141">Debugging</span></span>](index.md)
