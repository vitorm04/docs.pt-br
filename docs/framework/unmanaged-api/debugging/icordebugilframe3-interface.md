---
title: Interface ICorDebugILFrame3
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b46c74ec0bfc1fc44bcaca07439c472b0fd8393f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946429"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="1b02d-102">Interface ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="1b02d-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="1b02d-103">Fornece um método que encapsula o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="1b02d-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="1b02d-104">`ICorDebugILFrame3` é uma extensão lógica das interfaces ICorDebugILFrame e ICorDebugILFrame2.</span><span class="sxs-lookup"><span data-stu-id="1b02d-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b02d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="1b02d-105">Methods</span></span>  
  
|<span data-ttu-id="1b02d-106">Método</span><span class="sxs-lookup"><span data-stu-id="1b02d-106">Method</span></span>|<span data-ttu-id="1b02d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b02d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b02d-108">Método GetReturnValueForILOffset</span><span class="sxs-lookup"><span data-stu-id="1b02d-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="1b02d-109">Obtém um objeto ICorDebugValue que encapsula o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="1b02d-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b02d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b02d-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b02d-111">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="1b02d-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b02d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1b02d-112">Requirements</span></span>  
 <span data-ttu-id="1b02d-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b02d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b02d-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b02d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b02d-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b02d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b02d-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b02d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b02d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b02d-117">See also</span></span>

- [<span data-ttu-id="1b02d-118">Interface ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="1b02d-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="1b02d-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1b02d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
