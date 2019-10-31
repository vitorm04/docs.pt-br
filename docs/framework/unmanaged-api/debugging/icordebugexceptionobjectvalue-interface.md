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
ms.openlocfilehash: a5762079861f04e1869b206c3200c3a024c1b77a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091005"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="eba14-102">Interface ICorDebugExceptionObjectValue</span><span class="sxs-lookup"><span data-stu-id="eba14-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="eba14-103">Estende a interface "ICorDebugObjectValue" para fornecer informações de rastreamento de pilha de um objeto de exceção gerenciado.</span><span class="sxs-lookup"><span data-stu-id="eba14-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eba14-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="eba14-104">Methods</span></span>  
  
|<span data-ttu-id="eba14-105">Método</span><span class="sxs-lookup"><span data-stu-id="eba14-105">Method</span></span>|<span data-ttu-id="eba14-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="eba14-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eba14-107">Método EnumerateExceptionCallStack</span><span class="sxs-lookup"><span data-stu-id="eba14-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="eba14-108">Obtém um enumerador para a pilha de chamadas inserido em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="eba14-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eba14-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="eba14-109">Remarks</span></span>  
 <span data-ttu-id="eba14-110">A chamada para `QueryInterface` terá sucesso para objetos gerenciados que derivam de <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="eba14-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eba14-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eba14-111">Requirements</span></span>  
 <span data-ttu-id="eba14-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eba14-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eba14-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eba14-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eba14-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eba14-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eba14-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eba14-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba14-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eba14-116">See also</span></span>

- [<span data-ttu-id="eba14-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="eba14-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="eba14-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="eba14-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
