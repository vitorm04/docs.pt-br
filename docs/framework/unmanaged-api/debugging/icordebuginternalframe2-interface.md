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
ms.openlocfilehash: 2cf75de6a71cfbe25cbde281f837060b88e93753
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087229"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="b01a6-102">Interface ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="b01a6-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="b01a6-103">Fornece informações sobre os quadros internos, incluindo o endereço de pilha e a posição em relação aos objetos ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="b01a6-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b01a6-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b01a6-104">Methods</span></span>  
  
|<span data-ttu-id="b01a6-105">Método</span><span class="sxs-lookup"><span data-stu-id="b01a6-105">Method</span></span>|<span data-ttu-id="b01a6-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b01a6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b01a6-107">Método GetFrameAddress</span><span class="sxs-lookup"><span data-stu-id="b01a6-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="b01a6-108">Retorna o endereço de pilha do quadro interno.</span><span class="sxs-lookup"><span data-stu-id="b01a6-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="b01a6-109">Método IsCloserToLeaf</span><span class="sxs-lookup"><span data-stu-id="b01a6-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="b01a6-110">Verifica se o `this` quadro interno está mais próximo da folha que o objeto ICorDebugFrame especificado.</span><span class="sxs-lookup"><span data-stu-id="b01a6-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b01a6-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b01a6-111">Remarks</span></span>  
 <span data-ttu-id="b01a6-112">Essa interface estende a interface ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="b01a6-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b01a6-113">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="b01a6-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b01a6-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b01a6-114">Requirements</span></span>  
 <span data-ttu-id="b01a6-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b01a6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b01a6-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b01a6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b01a6-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b01a6-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b01a6-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b01a6-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b01a6-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b01a6-119">See also</span></span>

- [<span data-ttu-id="b01a6-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b01a6-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b01a6-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="b01a6-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
