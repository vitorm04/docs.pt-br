---
title: Método IHostTaskManager::GetStackGuarantee
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad95f8ee5188c38bb19882d3c7fa6bf98fcc9d2a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625244"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="deb53-102">Método IHostTaskManager::GetStackGuarantee</span><span class="sxs-lookup"><span data-stu-id="deb53-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="deb53-103">Obtém a quantidade de espaço de pilha é certamente estarão disponíveis após a conclusão de uma operação de pilha, mas antes do fechamento de um processo.</span><span class="sxs-lookup"><span data-stu-id="deb53-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deb53-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="deb53-104">Syntax</span></span>  
  
```  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="deb53-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="deb53-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="deb53-106">[out] Um ponteiro para o número de bytes que estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="deb53-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deb53-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="deb53-107">Requirements</span></span>  
 <span data-ttu-id="deb53-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="deb53-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deb53-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="deb53-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="deb53-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="deb53-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="deb53-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deb53-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deb53-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="deb53-112">See also</span></span>
- [<span data-ttu-id="deb53-113">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="deb53-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
