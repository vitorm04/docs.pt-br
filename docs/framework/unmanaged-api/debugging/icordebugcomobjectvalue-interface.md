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
ms.openlocfilehash: 8d339d3146a8a9214c3518eac6c31ed5222f9b31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="324d0-102">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="324d0-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="324d0-103">Fornece métodos para recuperar as informações associadas a um runtime callable wrapper (RCW).</span><span class="sxs-lookup"><span data-stu-id="324d0-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="324d0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="324d0-104">Methods</span></span>  
  
|<span data-ttu-id="324d0-105">Método</span><span class="sxs-lookup"><span data-stu-id="324d0-105">Method</span></span>|<span data-ttu-id="324d0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="324d0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="324d0-107">Método GetCachedInterfacePointers</span><span class="sxs-lookup"><span data-stu-id="324d0-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="324d0-108">Obtém os ponteiros de interface bruto em cache no RCW atual.</span><span class="sxs-lookup"><span data-stu-id="324d0-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="324d0-109">Método GetCachedInterfaceTypes</span><span class="sxs-lookup"><span data-stu-id="324d0-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="324d0-110">Fornece um enumerador para os tipos de interface que o objeto atual foi maiusculas e minúsculas para ou usado como.</span><span class="sxs-lookup"><span data-stu-id="324d0-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="324d0-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="324d0-111">Remarks</span></span>  
 <span data-ttu-id="324d0-112">Para verificar se uma instância de uma interface de "ICorDebugValue" representa um RCW, chama um depurador `QueryInterface` em "ICorDebugValue" com `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="324d0-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="324d0-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="324d0-113">Requirements</span></span>  
 <span data-ttu-id="324d0-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="324d0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="324d0-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="324d0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="324d0-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="324d0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="324d0-117">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="324d0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="324d0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="324d0-118">See Also</span></span>  
 [<span data-ttu-id="324d0-119">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="324d0-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="324d0-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="324d0-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
