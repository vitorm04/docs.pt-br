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
ms.openlocfilehash: 9a768535c3bf69b5127777de4cee27054943091d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793637"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="7944b-102">Interface ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="7944b-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="7944b-103">Fornece métodos que manipulam os módulos de carregamento e descarregamento para depuração.</span><span class="sxs-lookup"><span data-stu-id="7944b-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7944b-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7944b-104">Methods</span></span>  
  
|<span data-ttu-id="7944b-105">Método</span><span class="sxs-lookup"><span data-stu-id="7944b-105">Method</span></span>|<span data-ttu-id="7944b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7944b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7944b-107">Método OpenVirtualProcess</span><span class="sxs-lookup"><span data-stu-id="7944b-107">OpenVirtualProcess Method</span></span>](iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="7944b-108">Obtém a interface "ICorDebugProcess" que corresponde a um módulo Common Language Runtime (CLR) carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="7944b-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="7944b-109">Método CanUnloadNow</span><span class="sxs-lookup"><span data-stu-id="7944b-109">CanUnloadNow Method</span></span>](iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="7944b-110">Determina se uma biblioteca fornecida por uma interface [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) ainda está em uso ou pode ser descarregada.</span><span class="sxs-lookup"><span data-stu-id="7944b-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7944b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="7944b-111">Remarks</span></span>  
 <span data-ttu-id="7944b-112">Você pode obter uma instância da interface `ICLRDebugging` usando a função [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) .</span><span class="sxs-lookup"><span data-stu-id="7944b-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7944b-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="7944b-113">Requirements</span></span>  
 <span data-ttu-id="7944b-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7944b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7944b-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7944b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7944b-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7944b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7944b-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7944b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7944b-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="7944b-118">See also</span></span>

- [<span data-ttu-id="7944b-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7944b-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7944b-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="7944b-120">Debugging</span></span>](index.md)
