---
title: Interface ICorDebugComObjectValue
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugComObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugComObjectValue
helpviewer_keywords: ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9adeec14e102ef575f24566980477a285f87ba40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="14777-102">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="14777-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="14777-103">Fornece métodos para recuperar as informações associadas a um runtime callable wrapper (RCW).</span><span class="sxs-lookup"><span data-stu-id="14777-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="14777-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="14777-104">Methods</span></span>  
  
|<span data-ttu-id="14777-105">Método</span><span class="sxs-lookup"><span data-stu-id="14777-105">Method</span></span>|<span data-ttu-id="14777-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="14777-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="14777-107">Método GetCachedInterfacePointers</span><span class="sxs-lookup"><span data-stu-id="14777-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="14777-108">Obtém os ponteiros de interface bruto em cache no RCW atual.</span><span class="sxs-lookup"><span data-stu-id="14777-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="14777-109">Método GetCachedInterfaceTypes</span><span class="sxs-lookup"><span data-stu-id="14777-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="14777-110">Fornece um enumerador para os tipos de interface que o objeto atual foi maiusculas e minúsculas para ou usado como.</span><span class="sxs-lookup"><span data-stu-id="14777-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14777-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="14777-111">Remarks</span></span>  
 <span data-ttu-id="14777-112">Para verificar se uma instância de uma interface de "ICorDebugValue" representa um RCW, chama um depurador `QueryInterface` em "ICorDebugValue" com `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="14777-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14777-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="14777-113">Requirements</span></span>  
 <span data-ttu-id="14777-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14777-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14777-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14777-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14777-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14777-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14777-117">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14777-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14777-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14777-118">See Also</span></span>  
 [<span data-ttu-id="14777-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="14777-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="14777-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="14777-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
