---
title: Método IHostTask::Start
ms.date: 03/30/2017
api_name:
- IHostTask.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bc996973a98f3b8596b449e1524d5c93b4456e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749812"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="f8245-102">Método IHostTask::Start</span><span class="sxs-lookup"><span data-stu-id="f8245-102">IHostTask::Start Method</span></span>
<span data-ttu-id="f8245-103">Solicitações que o host de move a tarefa representada por atual [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância de um suspenso para um estado ativo, no qual o código pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="f8245-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8245-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8245-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f8245-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f8245-105">Return Value</span></span>  
  
|<span data-ttu-id="f8245-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f8245-106">HRESULT</span></span>|<span data-ttu-id="f8245-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8245-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f8245-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f8245-108">S_OK</span></span>|<span data-ttu-id="f8245-109">Iniciar retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f8245-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="f8245-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f8245-110">E_FAIL</span></span>|<span data-ttu-id="f8245-111">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f8245-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f8245-112">Quando um método retornar E_FAIL, o common language runtime (CLR) não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="f8245-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="f8245-113">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f8245-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8245-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="f8245-114">Remarks</span></span>  
 <span data-ttu-id="f8245-115">`Start` sempre retorna um valor HRESULT de S_OK, exceto em casos em que ocorreu uma falha catastrófica.</span><span class="sxs-lookup"><span data-stu-id="f8245-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8245-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f8245-116">Requirements</span></span>  
 <span data-ttu-id="f8245-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8245-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8245-118">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f8245-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8245-119">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f8245-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8245-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8245-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8245-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8245-121">See also</span></span>

- [<span data-ttu-id="f8245-122">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="f8245-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f8245-123">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="f8245-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f8245-124">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="f8245-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="f8245-125">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="f8245-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
