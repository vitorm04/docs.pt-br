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
ms.openlocfilehash: 4db005e1de043e60ffe958de732a5280fcccbea7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529941"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="df266-102">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="df266-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="df266-103">Fornece métodos para recuperar as informações associadas a um runtime callable wrapper (RCW).</span><span class="sxs-lookup"><span data-stu-id="df266-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df266-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="df266-104">Methods</span></span>  
  
|<span data-ttu-id="df266-105">Método</span><span class="sxs-lookup"><span data-stu-id="df266-105">Method</span></span>|<span data-ttu-id="df266-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="df266-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df266-107">Método GetCachedInterfacePointers</span><span class="sxs-lookup"><span data-stu-id="df266-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="df266-108">Obtém os ponteiros de interface bruto armazenado em cache no RCW atual.</span><span class="sxs-lookup"><span data-stu-id="df266-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="df266-109">Método GetCachedInterfaceTypes</span><span class="sxs-lookup"><span data-stu-id="df266-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="df266-110">Fornece um enumerador para os tipos de interface que o objeto atual foi maiusculas e minúsculas para ou usado como.</span><span class="sxs-lookup"><span data-stu-id="df266-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df266-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="df266-111">Remarks</span></span>  
 <span data-ttu-id="df266-112">Para verificar se uma instância de uma interface "ICorDebugValue" representa um RCW, chama um depurador `QueryInterface` em "ICorDebugValue" com `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="df266-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df266-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df266-113">Requirements</span></span>  
 <span data-ttu-id="df266-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df266-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df266-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df266-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df266-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df266-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df266-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df266-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df266-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df266-118">See also</span></span>
- [<span data-ttu-id="df266-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="df266-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="df266-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="df266-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
