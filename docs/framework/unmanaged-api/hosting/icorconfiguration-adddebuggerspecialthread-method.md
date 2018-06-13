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
ms.openlocfilehash: 59b940c0dbe9462dda513e933b7360ff55a9b447
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437343"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="ad6c1-102">Método ICorConfiguration::AddDebuggerSpecialThread</span><span class="sxs-lookup"><span data-stu-id="ad6c1-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="ad6c1-103">Para os serviços de depuração, indica que um determinado thread deve ter permissão para continuar em execução enquanto o depurador tem um aplicativo interrompido durante a cenários de depuração gerenciados ou não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="ad6c1-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad6c1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad6c1-104">Syntax</span></span>  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad6c1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ad6c1-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="ad6c1-106">[in] A ID do thread que deve ter permissão para continuar a executar.</span><span class="sxs-lookup"><span data-stu-id="ad6c1-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad6c1-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ad6c1-107">Remarks</span></span>  
 <span data-ttu-id="ad6c1-108">O thread especificado não poderá executar código gerenciado ou inserir o tempo de execução de qualquer maneira.</span><span class="sxs-lookup"><span data-stu-id="ad6c1-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="ad6c1-109">Um exemplo de tal thread seria um thread no processo para dar suporte a script herdados depuradores.</span><span class="sxs-lookup"><span data-stu-id="ad6c1-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad6c1-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad6c1-110">Requirements</span></span>  
 <span data-ttu-id="ad6c1-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad6c1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad6c1-112">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ad6c1-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ad6c1-113">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ad6c1-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad6c1-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad6c1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad6c1-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad6c1-115">See Also</span></span>  
 [<span data-ttu-id="ad6c1-116">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="ad6c1-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
