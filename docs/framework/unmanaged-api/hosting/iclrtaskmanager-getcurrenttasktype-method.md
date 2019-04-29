---
title: Método ICLRTaskManager::GetCurrentTaskType
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTaskType
helpviewer_keywords:
- GetCurrentTaskType method [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTaskType method [.NET Framework hosting]
ms.assetid: 6b0d9259-dbe2-45bb-b34d-990f60c73424
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2963e2a31fd62470e3ed6933edb38119d286071b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763354"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="b12b0-102">Método ICLRTaskManager::GetCurrentTaskType</span><span class="sxs-lookup"><span data-stu-id="b12b0-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>
<span data-ttu-id="b12b0-103">Obtém o tipo da tarefa que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="b12b0-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b12b0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b12b0-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b12b0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b12b0-105">Parameters</span></span>  
 `pTaskType`  
 <span data-ttu-id="b12b0-106">[out] Um ponteiro para um valor igual a [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) enumeração que indica o tipo de tarefa que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="b12b0-106">[out] A pointer to a value of the [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b12b0-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b12b0-107">Requirements</span></span>  
 <span data-ttu-id="b12b0-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b12b0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b12b0-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b12b0-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b12b0-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b12b0-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b12b0-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b12b0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b12b0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b12b0-112">See also</span></span>

- [<span data-ttu-id="b12b0-113">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="b12b0-113">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
