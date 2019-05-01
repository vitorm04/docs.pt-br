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
ms.openlocfilehash: b5328442ceaee05b3f81466b785f04a361d456a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995911"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="a192a-102">Interface ICorDebugExceptionObjectValue</span><span class="sxs-lookup"><span data-stu-id="a192a-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="a192a-103">Estende a interface "ICorDebugObjectValue" para fornecer informações de rastreamento de pilha de um objeto de exceção gerenciada.</span><span class="sxs-lookup"><span data-stu-id="a192a-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a192a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a192a-104">Methods</span></span>  
  
|<span data-ttu-id="a192a-105">Método</span><span class="sxs-lookup"><span data-stu-id="a192a-105">Method</span></span>|<span data-ttu-id="a192a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a192a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a192a-107">Método EnumerateExceptionCallStack</span><span class="sxs-lookup"><span data-stu-id="a192a-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="a192a-108">Obtém um enumerador para a pilha de chamadas inserida em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="a192a-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a192a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a192a-109">Remarks</span></span>  
 <span data-ttu-id="a192a-110">A chamada para `QueryInterface` terá êxito para os objetos gerenciados que derivam de <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a192a-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a192a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a192a-111">Requirements</span></span>  
 <span data-ttu-id="a192a-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a192a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a192a-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a192a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a192a-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a192a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a192a-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a192a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a192a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a192a-116">See also</span></span>

- [<span data-ttu-id="a192a-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a192a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a192a-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="a192a-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
