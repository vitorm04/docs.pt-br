---
title: Interface ICorDebugFunction3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 28d2d0d1058dae69bc17e370cc42ed56dc35b0e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="f2b25-102">Interface ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="f2b25-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="f2b25-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="f2b25-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f2b25-104">Logicamente estende a interface ICorDebugFunction para fornecer acesso ao código de uma solicitação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="f2b25-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f2b25-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="f2b25-105">Methods</span></span>  
  
|<span data-ttu-id="f2b25-106">Método</span><span class="sxs-lookup"><span data-stu-id="f2b25-106">Method</span></span>|<span data-ttu-id="f2b25-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2b25-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f2b25-108">Método GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="f2b25-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="f2b25-109">Obtém um ponteiro de interface para um [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) que contém o IL de uma solicitação ReJIT ativa.</span><span class="sxs-lookup"><span data-stu-id="f2b25-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2b25-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f2b25-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2b25-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2b25-111">Requirements</span></span>  
 <span data-ttu-id="f2b25-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2b25-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2b25-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2b25-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2b25-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2b25-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2b25-115">**Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2b25-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b25-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2b25-116">See Also</span></span>  
 [<span data-ttu-id="f2b25-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f2b25-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f2b25-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="f2b25-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 [<span data-ttu-id="f2b25-119">ReJIT: Um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="f2b25-119">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
