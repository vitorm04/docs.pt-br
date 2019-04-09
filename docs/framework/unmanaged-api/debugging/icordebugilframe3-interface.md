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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113757"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="0d8d2-102">Interface ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="0d8d2-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="0d8d2-103">Fornece um método que encapsula o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="0d8d2-103">Provides a method that encapsulates the return value of a function.</span></span> `ICorDebugILFrame3` <span data-ttu-id="0d8d2-104">é uma extensão lógica das interfaces ICorDebugILFrame e ICorDebugILFrame2.</span><span class="sxs-lookup"><span data-stu-id="0d8d2-104">is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0d8d2-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="0d8d2-105">Methods</span></span>  
  
|<span data-ttu-id="0d8d2-106">Método</span><span class="sxs-lookup"><span data-stu-id="0d8d2-106">Method</span></span>|<span data-ttu-id="0d8d2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d8d2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0d8d2-108">Método GetReturnValueForILOffset</span><span class="sxs-lookup"><span data-stu-id="0d8d2-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="0d8d2-109">Obtém um objeto ICorDebugValue que encapsula o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="0d8d2-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d8d2-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d8d2-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d8d2-111">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="0d8d2-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d8d2-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d8d2-112">Requirements</span></span>  
 <span data-ttu-id="0d8d2-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d8d2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d8d2-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d8d2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d8d2-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d8d2-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0d8d2-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="0d8d2-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0d8d2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d8d2-117">See also</span></span>

- [<span data-ttu-id="0d8d2-118">Interface ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="0d8d2-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="0d8d2-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="0d8d2-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
