---
title: Interface ICorDebugMemoryBuffer
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e12b50e964ec470b843ae35c960f20c5675fd572
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072903"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="a2a8a-102">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="a2a8a-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="a2a8a-103">Representa um buffer na memória.</span><span class="sxs-lookup"><span data-stu-id="a2a8a-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a2a8a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a2a8a-104">Methods</span></span>  
  
|<span data-ttu-id="a2a8a-105">Método</span><span class="sxs-lookup"><span data-stu-id="a2a8a-105">Method</span></span>|<span data-ttu-id="a2a8a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2a8a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a2a8a-107">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="a2a8a-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="a2a8a-108">Obtém o tamanho do buffer de memória em bytes.</span><span class="sxs-lookup"><span data-stu-id="a2a8a-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="a2a8a-109">Método GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="a2a8a-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="a2a8a-110">Obtém o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="a2a8a-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2a8a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2a8a-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2a8a-112">Essa interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a2a8a-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="a2a8a-113">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="a2a8a-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2a8a-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a2a8a-114">Requirements</span></span>  
 <span data-ttu-id="a2a8a-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2a8a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2a8a-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2a8a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2a8a-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2a8a-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a2a8a-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a2a8a-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a2a8a-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2a8a-119">See also</span></span>

- [<span data-ttu-id="a2a8a-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a2a8a-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a2a8a-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="a2a8a-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
