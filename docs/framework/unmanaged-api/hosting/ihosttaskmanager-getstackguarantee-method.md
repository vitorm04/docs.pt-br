---
title: "Método IHostTaskManager::GetStackGuarantee"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostTaskManager.GetStackGuarantee
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetStackGuarantee
helpviewer_keywords:
- GetStackGuarantee method [.NET Framework hosting]
- IHostTaskManager::GetStackGuarantee method [.NET Framework hosting]
ms.assetid: 8176d732-c25c-4520-811d-e3310f339947
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a2e4829083715fad8d77c1b5a2c303a07d5684ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="9451e-102">Método IHostTaskManager::GetStackGuarantee</span><span class="sxs-lookup"><span data-stu-id="9451e-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="9451e-103">Obtém a quantidade de espaço de pilha é a garantia de estar disponível após a conclusão de uma operação de pilha, mas antes do fechamento de um processo.</span><span class="sxs-lookup"><span data-stu-id="9451e-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9451e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9451e-104">Syntax</span></span>  
  
```  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9451e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9451e-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="9451e-106">[out] Um ponteiro para o número de bytes que estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9451e-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9451e-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9451e-107">Requirements</span></span>  
 <span data-ttu-id="9451e-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9451e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9451e-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9451e-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9451e-110">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9451e-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9451e-111">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9451e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9451e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9451e-112">See Also</span></span>  
 [<span data-ttu-id="9451e-113">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="9451e-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
