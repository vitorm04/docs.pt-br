---
title: Interface ICLRDebugging
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugging
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebugging
helpviewer_keywords: ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ac3e061b95faafeec3c3d233ab54f128a23c3264
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="a16c0-102">Interface ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="a16c0-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="a16c0-103">Fornece métodos que manipulam os módulos de carregamento e descarregamento para depuração.</span><span class="sxs-lookup"><span data-stu-id="a16c0-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a16c0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a16c0-104">Methods</span></span>  
  
|<span data-ttu-id="a16c0-105">Método</span><span class="sxs-lookup"><span data-stu-id="a16c0-105">Method</span></span>|<span data-ttu-id="a16c0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a16c0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a16c0-107">Método OpenVirtualProcess</span><span class="sxs-lookup"><span data-stu-id="a16c0-107">OpenVirtualProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="a16c0-108">Obtém a interface "ICorDebugProcess" que corresponde a um módulo de runtime (CLR) de linguagem comum carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="a16c0-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="a16c0-109">Método CanUnloadNow</span><span class="sxs-lookup"><span data-stu-id="a16c0-109">CanUnloadNow Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="a16c0-110">Determina se uma biblioteca que foi fornecida por um [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface ainda está em uso ou pode ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="a16c0-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a16c0-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="a16c0-111">Remarks</span></span>  
 <span data-ttu-id="a16c0-112">Você pode obter uma instância do `ICLRDebugging` interface usando o [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="a16c0-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a16c0-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a16c0-113">Requirements</span></span>  
 <span data-ttu-id="a16c0-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a16c0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a16c0-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a16c0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a16c0-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a16c0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a16c0-117">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a16c0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a16c0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a16c0-118">See Also</span></span>  
 [<span data-ttu-id="a16c0-119">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="a16c0-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a16c0-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="a16c0-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
