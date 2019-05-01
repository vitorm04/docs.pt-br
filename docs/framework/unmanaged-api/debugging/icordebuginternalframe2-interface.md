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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988436"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="45f04-102">Interface ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="45f04-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="45f04-103">Fornece informações sobre os quadros internos, incluindo o endereço de pilha e a posição em relação aos objetos ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="45f04-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="45f04-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="45f04-104">Methods</span></span>  
  
|<span data-ttu-id="45f04-105">Método</span><span class="sxs-lookup"><span data-stu-id="45f04-105">Method</span></span>|<span data-ttu-id="45f04-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="45f04-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45f04-107">Método GetFrameAddress</span><span class="sxs-lookup"><span data-stu-id="45f04-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="45f04-108">Retorna o endereço de pilha do quadro interno.</span><span class="sxs-lookup"><span data-stu-id="45f04-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="45f04-109">Método IsCloserToLeaf</span><span class="sxs-lookup"><span data-stu-id="45f04-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="45f04-110">Verifica se o `this` quadro interno está mais próximo da folha que o objeto ICorDebugFrame especificado.</span><span class="sxs-lookup"><span data-stu-id="45f04-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45f04-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="45f04-111">Remarks</span></span>  
 <span data-ttu-id="45f04-112">Essa interface estende a interface ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="45f04-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45f04-113">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="45f04-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45f04-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45f04-114">Requirements</span></span>  
 <span data-ttu-id="45f04-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45f04-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45f04-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45f04-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45f04-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45f04-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45f04-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45f04-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45f04-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45f04-119">See also</span></span>

- [<span data-ttu-id="45f04-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="45f04-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="45f04-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="45f04-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
