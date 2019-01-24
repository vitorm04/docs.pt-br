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
ms.openlocfilehash: ec781a4b51b425225339c08ec8fa194da1972462
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625687"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="087d6-102">Método IHostTask::Start</span><span class="sxs-lookup"><span data-stu-id="087d6-102">IHostTask::Start Method</span></span>
<span data-ttu-id="087d6-103">Solicitações que o host de move a tarefa representada por atual [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância de um suspenso para um estado ativo, no qual o código pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="087d6-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="087d6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="087d6-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="087d6-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="087d6-105">Return Value</span></span>  
  
|<span data-ttu-id="087d6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="087d6-106">HRESULT</span></span>|<span data-ttu-id="087d6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="087d6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="087d6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="087d6-108">S_OK</span></span>|<span data-ttu-id="087d6-109">Iniciar retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="087d6-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="087d6-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="087d6-110">E_FAIL</span></span>|<span data-ttu-id="087d6-111">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="087d6-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="087d6-112">Quando um método retornar E_FAIL, o common language runtime (CLR) não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="087d6-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="087d6-113">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="087d6-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="087d6-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="087d6-114">Remarks</span></span>  
 <span data-ttu-id="087d6-115">`Start` sempre retorna um valor HRESULT de S_OK, exceto em casos em que ocorreu uma falha catastrófica.</span><span class="sxs-lookup"><span data-stu-id="087d6-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="087d6-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="087d6-116">Requirements</span></span>  
 <span data-ttu-id="087d6-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="087d6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="087d6-118">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="087d6-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="087d6-119">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="087d6-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="087d6-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="087d6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="087d6-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="087d6-121">See also</span></span>
- [<span data-ttu-id="087d6-122">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="087d6-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="087d6-123">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="087d6-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="087d6-124">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="087d6-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="087d6-125">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="087d6-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
