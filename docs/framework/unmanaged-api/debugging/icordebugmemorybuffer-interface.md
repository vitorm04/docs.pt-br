---
title: Interface ICorDebugMemoryBuffer
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: 60f3b0c3230c524ca7d308d3cb80e50b0693715d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212328"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="95392-102">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="95392-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="95392-103">Representa um buffer na memória.</span><span class="sxs-lookup"><span data-stu-id="95392-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95392-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="95392-104">Methods</span></span>  
  
|<span data-ttu-id="95392-105">Método</span><span class="sxs-lookup"><span data-stu-id="95392-105">Method</span></span>|<span data-ttu-id="95392-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="95392-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95392-107">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="95392-107">GetSize Method</span></span>](icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="95392-108">Obtém o tamanho do buffer de memória em bytes.</span><span class="sxs-lookup"><span data-stu-id="95392-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="95392-109">Método GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="95392-109">GetStartAddress Method</span></span>](icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="95392-110">Obtém o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="95392-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95392-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="95392-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95392-112">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="95392-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="95392-113">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="95392-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95392-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95392-114">Requirements</span></span>  
 <span data-ttu-id="95392-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95392-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95392-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95392-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95392-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95392-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95392-118">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95392-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95392-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="95392-119">See also</span></span>

- [<span data-ttu-id="95392-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="95392-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="95392-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="95392-121">Debugging</span></span>](index.md)
