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
ms.openlocfilehash: 848255d44ce8637182f18288d30151a3f0df0912
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092161"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="fccf6-102">Método ICLRTaskManager::GetCurrentTaskType</span><span class="sxs-lookup"><span data-stu-id="fccf6-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>
<span data-ttu-id="fccf6-103">Obtém o tipo da tarefa que está sendo executada no momento.</span><span class="sxs-lookup"><span data-stu-id="fccf6-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fccf6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fccf6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fccf6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fccf6-105">Parameters</span></span>  
 `pTaskType`  
 <span data-ttu-id="fccf6-106">fora Um ponteiro para um valor da enumeração [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) que indica o tipo de tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="fccf6-106">[out] A pointer to a value of the [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fccf6-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fccf6-107">Requirements</span></span>  
 <span data-ttu-id="fccf6-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fccf6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fccf6-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fccf6-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fccf6-110">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fccf6-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fccf6-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fccf6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fccf6-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fccf6-112">See also</span></span>

- [<span data-ttu-id="fccf6-113">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="fccf6-113">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
