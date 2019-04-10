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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db1b19c1499f7e8a126933b4d0635a0ab73e72a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218583"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="929e8-102">Método ICorConfiguration::AddDebuggerSpecialThread</span><span class="sxs-lookup"><span data-stu-id="929e8-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="929e8-103">Para os serviços de depuração, indica que um thread específico deve ter permissão para continuar em execução enquanto o depurador tem um aplicativo interrompido durante cenários de depuração gerenciados ou não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="929e8-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="929e8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="929e8-104">Syntax</span></span>  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="929e8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="929e8-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="929e8-106">[in] A ID do thread que deve ter permissão para continuar a executar.</span><span class="sxs-lookup"><span data-stu-id="929e8-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="929e8-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="929e8-107">Remarks</span></span>  
 <span data-ttu-id="929e8-108">O thread especificado será permitido para executar código gerenciado ou inserir o tempo de execução de qualquer maneira.</span><span class="sxs-lookup"><span data-stu-id="929e8-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="929e8-109">Um exemplo de tal thread seria um thread no processo para dar suporte a depuradores de script herdados.</span><span class="sxs-lookup"><span data-stu-id="929e8-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="929e8-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="929e8-110">Requirements</span></span>  
 <span data-ttu-id="929e8-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="929e8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="929e8-112">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="929e8-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="929e8-113">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="929e8-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="929e8-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="929e8-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="929e8-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="929e8-115">See also</span></span>

- [<span data-ttu-id="929e8-116">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="929e8-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
