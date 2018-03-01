---
title: Interface ICLRDebugging
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 325f6adf8fe3a357f903f0cb047a2255ef80e264
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="066f8-102">Interface ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="066f8-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="066f8-103">Fornece métodos que manipulam os módulos de carregamento e descarregamento para depuração.</span><span class="sxs-lookup"><span data-stu-id="066f8-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="066f8-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="066f8-104">Methods</span></span>  
  
|<span data-ttu-id="066f8-105">Método</span><span class="sxs-lookup"><span data-stu-id="066f8-105">Method</span></span>|<span data-ttu-id="066f8-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="066f8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="066f8-107">Método OpenVirtualProcess</span><span class="sxs-lookup"><span data-stu-id="066f8-107">OpenVirtualProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="066f8-108">Obtém a interface "ICorDebugProcess" que corresponde a um módulo de runtime (CLR) de linguagem comum carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="066f8-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="066f8-109">Método CanUnloadNow</span><span class="sxs-lookup"><span data-stu-id="066f8-109">CanUnloadNow Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="066f8-110">Determina se uma biblioteca que foi fornecida por um [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface ainda está em uso ou pode ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="066f8-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="066f8-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="066f8-111">Remarks</span></span>  
 <span data-ttu-id="066f8-112">Você pode obter uma instância do `ICLRDebugging` interface usando o [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="066f8-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="066f8-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="066f8-113">Requirements</span></span>  
 <span data-ttu-id="066f8-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="066f8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="066f8-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="066f8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="066f8-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="066f8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="066f8-117">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="066f8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="066f8-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="066f8-118">See Also</span></span>  
 [<span data-ttu-id="066f8-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="066f8-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="066f8-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="066f8-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
