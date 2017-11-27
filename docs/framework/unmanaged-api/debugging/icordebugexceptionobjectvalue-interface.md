---
title: Interface ICorDebugExceptionObjectValue
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectValue
helpviewer_keywords: ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 47733a6af18d42d0d9db1e50cf21646289ef1443
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="00e75-102">Interface ICorDebugExceptionObjectValue</span><span class="sxs-lookup"><span data-stu-id="00e75-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="00e75-103">Estende a interface "ICorDebugObjectValue" para fornecer informações de rastreamento de pilha de um objeto de exceção gerenciada.</span><span class="sxs-lookup"><span data-stu-id="00e75-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00e75-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="00e75-104">Methods</span></span>  
  
|<span data-ttu-id="00e75-105">Método</span><span class="sxs-lookup"><span data-stu-id="00e75-105">Method</span></span>|<span data-ttu-id="00e75-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="00e75-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00e75-107">Método EnumerateExceptionCallStack</span><span class="sxs-lookup"><span data-stu-id="00e75-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="00e75-108">Obtém um enumerador para a pilha de chamadas incorporada em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="00e75-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00e75-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="00e75-109">Remarks</span></span>  
 <span data-ttu-id="00e75-110">A chamada para `QueryInterface` funcionará para os objetos gerenciados que derivam de <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="00e75-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00e75-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="00e75-111">Requirements</span></span>  
 <span data-ttu-id="00e75-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00e75-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00e75-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00e75-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00e75-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00e75-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00e75-115">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00e75-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00e75-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00e75-116">See Also</span></span>  
 [<span data-ttu-id="00e75-117">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="00e75-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="00e75-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="00e75-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 
