---
title: Interface ICorDebugMemoryBuffer
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: 9e43f9a2297eb56755c7a6bba73e994441cbfeaa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127971"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="ef5c7-102">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="ef5c7-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="ef5c7-103">Representa um buffer na memória.</span><span class="sxs-lookup"><span data-stu-id="ef5c7-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ef5c7-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ef5c7-104">Methods</span></span>  
  
|<span data-ttu-id="ef5c7-105">Método</span><span class="sxs-lookup"><span data-stu-id="ef5c7-105">Method</span></span>|<span data-ttu-id="ef5c7-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef5c7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ef5c7-107">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="ef5c7-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="ef5c7-108">Obtém o tamanho do buffer de memória em bytes.</span><span class="sxs-lookup"><span data-stu-id="ef5c7-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="ef5c7-109">Método GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="ef5c7-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="ef5c7-110">Obtém o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="ef5c7-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef5c7-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="ef5c7-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef5c7-112">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ef5c7-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="ef5c7-113">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="ef5c7-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef5c7-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ef5c7-114">Requirements</span></span>  
 <span data-ttu-id="ef5c7-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef5c7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef5c7-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef5c7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef5c7-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef5c7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef5c7-118">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef5c7-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef5c7-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef5c7-119">See also</span></span>

- [<span data-ttu-id="ef5c7-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ef5c7-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ef5c7-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="ef5c7-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
