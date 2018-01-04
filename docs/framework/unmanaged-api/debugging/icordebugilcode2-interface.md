---
title: Interface ICorDebugILCode2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILCode2
api_location: mscordbi.dll
api_type: COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f126d92cebe3261dc92b89cbf66bbcff5fd8808e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="003df-102">Interface ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="003df-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="003df-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="003df-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="003df-104">Logicamente estende o [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) deslocamentos de interface forneça métodos que retornam o token de assinatura de variável local de uma função, e que mapeiam instrumentada IL (intermediate language) do criador de perfil para o método original IL deslocamentos.</span><span class="sxs-lookup"><span data-stu-id="003df-104">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="003df-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="003df-105">Methods</span></span>  
  
|<span data-ttu-id="003df-106">Método</span><span class="sxs-lookup"><span data-stu-id="003df-106">Method</span></span>|<span data-ttu-id="003df-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="003df-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="003df-108">Método GetInstrumentedILMap</span><span class="sxs-lookup"><span data-stu-id="003df-108">GetInstrumentedILMap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="003df-109">Retorna um mapa de deslocamentos da IL instrumentada do criador de perfil para os deslocamentos da IL do método original para esta instância.</span><span class="sxs-lookup"><span data-stu-id="003df-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="003df-110">Método GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="003df-110">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="003df-111">Obtém o token de metadados para a assinatura de variável local para a função que é representada por esta instância.</span><span class="sxs-lookup"><span data-stu-id="003df-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="003df-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="003df-112">Requirements</span></span>  
 <span data-ttu-id="003df-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="003df-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="003df-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="003df-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="003df-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="003df-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="003df-116">**Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="003df-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="003df-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="003df-117">See Also</span></span>  
 [<span data-ttu-id="003df-118">Interface ICorDebugILCode</span><span class="sxs-lookup"><span data-stu-id="003df-118">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [<span data-ttu-id="003df-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="003df-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="003df-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="003df-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
