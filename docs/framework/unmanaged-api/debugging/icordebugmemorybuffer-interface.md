---
title: Interface ICorDebugMemoryBuffer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98703b07f6601307b5f26aa14b2faf67f8823be5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="cc7d3-102">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="cc7d3-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="cc7d3-103">Representa um buffer na memória.</span><span class="sxs-lookup"><span data-stu-id="cc7d3-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cc7d3-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="cc7d3-104">Methods</span></span>  
  
|<span data-ttu-id="cc7d3-105">Método</span><span class="sxs-lookup"><span data-stu-id="cc7d3-105">Method</span></span>|<span data-ttu-id="cc7d3-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc7d3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cc7d3-107">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="cc7d3-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="cc7d3-108">Obtém o tamanho do buffer de memória em bytes.</span><span class="sxs-lookup"><span data-stu-id="cc7d3-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="cc7d3-109">Método GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="cc7d3-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="cc7d3-110">Obtém o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="cc7d3-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc7d3-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc7d3-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc7d3-112">Esta interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cc7d3-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="cc7d3-113">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="cc7d3-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc7d3-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cc7d3-114">Requirements</span></span>  
 <span data-ttu-id="cc7d3-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc7d3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc7d3-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc7d3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc7d3-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc7d3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc7d3-118">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc7d3-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc7d3-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc7d3-119">See Also</span></span>  
 [<span data-ttu-id="cc7d3-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="cc7d3-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="cc7d3-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="cc7d3-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
