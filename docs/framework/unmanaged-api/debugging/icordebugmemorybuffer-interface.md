---
title: Interface ICorDebugMemoryBuffer
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: fa1bbca1e771cbc2b3475891862875b97b9e7f90
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793146"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="7abb0-102">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="7abb0-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="7abb0-103">Representa um buffer na memória.</span><span class="sxs-lookup"><span data-stu-id="7abb0-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7abb0-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7abb0-104">Methods</span></span>  
  
|<span data-ttu-id="7abb0-105">Método</span><span class="sxs-lookup"><span data-stu-id="7abb0-105">Method</span></span>|<span data-ttu-id="7abb0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7abb0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7abb0-107">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="7abb0-107">GetSize Method</span></span>](icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="7abb0-108">Obtém o tamanho do buffer de memória em bytes.</span><span class="sxs-lookup"><span data-stu-id="7abb0-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="7abb0-109">Método GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="7abb0-109">GetStartAddress Method</span></span>](icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="7abb0-110">Obtém o endereço inicial do buffer de memória.</span><span class="sxs-lookup"><span data-stu-id="7abb0-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7abb0-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="7abb0-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7abb0-112">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7abb0-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="7abb0-113">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="7abb0-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7abb0-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="7abb0-114">Requirements</span></span>  
 <span data-ttu-id="7abb0-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7abb0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7abb0-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7abb0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7abb0-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7abb0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7abb0-118">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7abb0-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7abb0-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="7abb0-119">See also</span></span>

- [<span data-ttu-id="7abb0-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7abb0-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7abb0-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="7abb0-121">Debugging</span></span>](index.md)
