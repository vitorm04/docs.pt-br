---
title: Interface ICorDebugFunction3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction3
api_location: mscordbi.dll
api_type: COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfe0c420c1c9b8074b7cb769e592f8cb2f5916e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="1f35c-102">Interface ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="1f35c-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="1f35c-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="1f35c-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="1f35c-104">Logicamente estende a interface ICorDebugFunction para fornecer acesso ao código de uma solicitação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="1f35c-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1f35c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="1f35c-105">Methods</span></span>  
  
|<span data-ttu-id="1f35c-106">Método</span><span class="sxs-lookup"><span data-stu-id="1f35c-106">Method</span></span>|<span data-ttu-id="1f35c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1f35c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1f35c-108">Método GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="1f35c-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="1f35c-109">Obtém um ponteiro de interface para um [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) que contém o IL de uma solicitação ReJIT ativa.</span><span class="sxs-lookup"><span data-stu-id="1f35c-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f35c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1f35c-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f35c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1f35c-111">Requirements</span></span>  
 <span data-ttu-id="1f35c-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f35c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f35c-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f35c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f35c-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f35c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f35c-115">**Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f35c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f35c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f35c-116">See Also</span></span>  
 [<span data-ttu-id="1f35c-117">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="1f35c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="1f35c-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="1f35c-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 [<span data-ttu-id="1f35c-119">ReJIT: Um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="1f35c-119">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
