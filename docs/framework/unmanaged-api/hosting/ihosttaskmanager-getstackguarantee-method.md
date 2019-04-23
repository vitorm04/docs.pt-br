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
ms.openlocfilehash: ea1c1f998febccbc80fb10cef5a8dfd229e1987e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095939"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="13c0b-102">Método IHostTaskManager::GetStackGuarantee</span><span class="sxs-lookup"><span data-stu-id="13c0b-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="13c0b-103">Obtém a quantidade de espaço de pilha é certamente estarão disponíveis após a conclusão de uma operação de pilha, mas antes do fechamento de um processo.</span><span class="sxs-lookup"><span data-stu-id="13c0b-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c0b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13c0b-104">Syntax</span></span>  
  
```  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13c0b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="13c0b-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="13c0b-106">[out] Um ponteiro para o número de bytes que estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="13c0b-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13c0b-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13c0b-107">Requirements</span></span>  
 <span data-ttu-id="13c0b-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13c0b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13c0b-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="13c0b-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13c0b-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="13c0b-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13c0b-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13c0b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c0b-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13c0b-112">See also</span></span>

- [<span data-ttu-id="13c0b-113">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="13c0b-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
