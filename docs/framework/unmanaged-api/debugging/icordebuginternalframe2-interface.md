---
title: Interface ICorDebugInternalFrame2
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2
helpviewer_keywords:
- ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2377773b471b387376f0284522ebe29d6b003ae3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910107"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="678b9-102">Interface ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="678b9-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="678b9-103">Fornece informações sobre quadros internos, incluindo o endereço de pilha e a posição em relação aos objetos ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="678b9-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="678b9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="678b9-104">Methods</span></span>  
  
|<span data-ttu-id="678b9-105">Método</span><span class="sxs-lookup"><span data-stu-id="678b9-105">Method</span></span>|<span data-ttu-id="678b9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="678b9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="678b9-107">Método GetFrameAddress</span><span class="sxs-lookup"><span data-stu-id="678b9-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="678b9-108">Retorna o endereço da pilha do quadro interno.</span><span class="sxs-lookup"><span data-stu-id="678b9-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="678b9-109">Método IsCloserToLeaf</span><span class="sxs-lookup"><span data-stu-id="678b9-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="678b9-110">Verifica se o `this` quadro interno está mais próximo da folha do que o objeto ICorDebugFrame especificado.</span><span class="sxs-lookup"><span data-stu-id="678b9-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="678b9-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="678b9-111">Remarks</span></span>  
 <span data-ttu-id="678b9-112">Essa interface estende a interface ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="678b9-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="678b9-113">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="678b9-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="678b9-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="678b9-114">Requirements</span></span>  
 <span data-ttu-id="678b9-115">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="678b9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="678b9-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="678b9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="678b9-117">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="678b9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="678b9-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="678b9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="678b9-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="678b9-119">See also</span></span>

- [<span data-ttu-id="678b9-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="678b9-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="678b9-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="678b9-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
