---
title: Interface ICorDebugExceptionObjectValue
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue
helpviewer_keywords:
- ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6805b7b49f76b80161aef5051fe3c284192f582
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413768"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="7a593-102">Interface ICorDebugExceptionObjectValue</span><span class="sxs-lookup"><span data-stu-id="7a593-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="7a593-103">Estende a interface "ICorDebugObjectValue" para fornecer informações de rastreamento de pilha de um objeto de exceção gerenciada.</span><span class="sxs-lookup"><span data-stu-id="7a593-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a593-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="7a593-104">Methods</span></span>  
  
|<span data-ttu-id="7a593-105">Método</span><span class="sxs-lookup"><span data-stu-id="7a593-105">Method</span></span>|<span data-ttu-id="7a593-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a593-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a593-107">Método EnumerateExceptionCallStack</span><span class="sxs-lookup"><span data-stu-id="7a593-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="7a593-108">Obtém um enumerador para a pilha de chamadas incorporada em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="7a593-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a593-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="7a593-109">Remarks</span></span>  
 <span data-ttu-id="7a593-110">A chamada para `QueryInterface` funcionará para os objetos gerenciados que derivam de <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7a593-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a593-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a593-111">Requirements</span></span>  
 <span data-ttu-id="7a593-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a593-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a593-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a593-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a593-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a593-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a593-115">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a593-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a593-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a593-116">See Also</span></span>  
 [<span data-ttu-id="7a593-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7a593-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7a593-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="7a593-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 
