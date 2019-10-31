---
title: Interface ICLRDebugging
ms.date: 03/30/2017
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
ms.openlocfilehash: 6506b11d97490f796486729dbeb612e47762b60a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111446"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="6c9a5-102">Interface ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="6c9a5-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="6c9a5-103">Fornece métodos que manipulam os módulos de carregamento e descarregamento para depuração.</span><span class="sxs-lookup"><span data-stu-id="6c9a5-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c9a5-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6c9a5-104">Methods</span></span>  
  
|<span data-ttu-id="6c9a5-105">Método</span><span class="sxs-lookup"><span data-stu-id="6c9a5-105">Method</span></span>|<span data-ttu-id="6c9a5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c9a5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c9a5-107">Método OpenVirtualProcess</span><span class="sxs-lookup"><span data-stu-id="6c9a5-107">OpenVirtualProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="6c9a5-108">Obtém a interface "ICorDebugProcess" que corresponde a um módulo Common Language Runtime (CLR) carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="6c9a5-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="6c9a5-109">Método CanUnloadNow</span><span class="sxs-lookup"><span data-stu-id="6c9a5-109">CanUnloadNow Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="6c9a5-110">Determina se uma biblioteca fornecida por uma interface [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) ainda está em uso ou pode ser descarregada.</span><span class="sxs-lookup"><span data-stu-id="6c9a5-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c9a5-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c9a5-111">Remarks</span></span>  
 <span data-ttu-id="6c9a5-112">Você pode obter uma instância da interface `ICLRDebugging` usando a função [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) .</span><span class="sxs-lookup"><span data-stu-id="6c9a5-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c9a5-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6c9a5-113">Requirements</span></span>  
 <span data-ttu-id="6c9a5-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c9a5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c9a5-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c9a5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c9a5-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c9a5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c9a5-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c9a5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c9a5-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c9a5-118">See also</span></span>

- [<span data-ttu-id="6c9a5-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6c9a5-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6c9a5-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="6c9a5-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
