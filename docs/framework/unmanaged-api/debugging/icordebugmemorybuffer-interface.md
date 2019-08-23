---
title: Interface ICorDebugMemoryBuffer
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77fa6b1a8c7a559b9d88c0173e389ec11a75ec8b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914782"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="7f052-102">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="7f052-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="7f052-103">Representa um buffer na memória.</span><span class="sxs-lookup"><span data-stu-id="7f052-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7f052-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="7f052-104">Methods</span></span>  
  
|<span data-ttu-id="7f052-105">Método</span><span class="sxs-lookup"><span data-stu-id="7f052-105">Method</span></span>|<span data-ttu-id="7f052-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f052-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7f052-107">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="7f052-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="7f052-108">Obtém o tamanho do buffer de memória em bytes.</span><span class="sxs-lookup"><span data-stu-id="7f052-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="7f052-109">Método GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="7f052-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="7f052-110">Obtém o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="7f052-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f052-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f052-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f052-112">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7f052-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="7f052-113">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="7f052-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f052-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f052-114">Requirements</span></span>  
 <span data-ttu-id="7f052-115">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f052-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f052-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f052-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f052-117">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f052-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f052-118">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f052-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f052-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f052-119">See also</span></span>

- [<span data-ttu-id="7f052-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7f052-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7f052-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="7f052-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
