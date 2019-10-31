---
title: Método ICorConfiguration::AddDebuggerSpecialThread
ms.date: 03/30/2017
api_name:
- ICorConfiguration.AddDebuggerSpecialThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type:
- apiref
ms.openlocfilehash: c5d6cfa3826667514eb70f9bb0df118d9ba0d07c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127813"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="46e82-102">Método ICorConfiguration::AddDebuggerSpecialThread</span><span class="sxs-lookup"><span data-stu-id="46e82-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="46e82-103">Indica aos serviços de depuração que um thread específico deve ter permissão para continuar a execução enquanto o depurador tem um aplicativo interrompido durante cenários de depuração gerenciados ou não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="46e82-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46e82-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="46e82-104">Syntax</span></span>  
  
```cpp  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46e82-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="46e82-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="46e82-106">no A ID do thread que deve ter permissão para continuar a execução.</span><span class="sxs-lookup"><span data-stu-id="46e82-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46e82-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="46e82-107">Remarks</span></span>  
 <span data-ttu-id="46e82-108">O thread especificado não terá permissão para executar código gerenciado ou inserir o tempo de execução de qualquer forma.</span><span class="sxs-lookup"><span data-stu-id="46e82-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="46e82-109">Um exemplo desse thread seria um thread em processo para dar suporte a depuradores de script herdados.</span><span class="sxs-lookup"><span data-stu-id="46e82-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46e82-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="46e82-110">Requirements</span></span>  
 <span data-ttu-id="46e82-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46e82-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46e82-112">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="46e82-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="46e82-113">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="46e82-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46e82-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46e82-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46e82-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46e82-115">See also</span></span>

- [<span data-ttu-id="46e82-116">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="46e82-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
