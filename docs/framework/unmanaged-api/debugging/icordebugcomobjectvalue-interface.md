---
title: Interface ICorDebugComObjectValue
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3387985ebf6027b9cd9dee372190da65939dbae3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098618"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="95c9f-102">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="95c9f-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="95c9f-103">Fornece métodos para recuperar as informações associadas a um runtime callable wrapper (RCW).</span><span class="sxs-lookup"><span data-stu-id="95c9f-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95c9f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="95c9f-104">Methods</span></span>  
  
|<span data-ttu-id="95c9f-105">Método</span><span class="sxs-lookup"><span data-stu-id="95c9f-105">Method</span></span>|<span data-ttu-id="95c9f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="95c9f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95c9f-107">Método GetCachedInterfacePointers</span><span class="sxs-lookup"><span data-stu-id="95c9f-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="95c9f-108">Obtém os ponteiros de interface bruto armazenado em cache no RCW atual.</span><span class="sxs-lookup"><span data-stu-id="95c9f-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="95c9f-109">Método GetCachedInterfaceTypes</span><span class="sxs-lookup"><span data-stu-id="95c9f-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="95c9f-110">Fornece um enumerador para os tipos de interface que o objeto atual foi maiusculas e minúsculas para ou usado como.</span><span class="sxs-lookup"><span data-stu-id="95c9f-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95c9f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="95c9f-111">Remarks</span></span>  
 <span data-ttu-id="95c9f-112">Para verificar se uma instância de uma interface "ICorDebugValue" representa um RCW, chama um depurador `QueryInterface` em "ICorDebugValue" com `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="95c9f-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95c9f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95c9f-113">Requirements</span></span>  
 <span data-ttu-id="95c9f-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95c9f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95c9f-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95c9f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95c9f-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95c9f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95c9f-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95c9f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c9f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95c9f-118">See also</span></span>

- [<span data-ttu-id="95c9f-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="95c9f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="95c9f-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="95c9f-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
