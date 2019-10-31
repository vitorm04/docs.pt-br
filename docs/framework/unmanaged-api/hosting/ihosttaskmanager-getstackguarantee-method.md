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
ms.openlocfilehash: 22ec34c82d0f8e550dfc8941f2c048ebed6cf1d7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133030"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="7f31f-102">Método IHostTaskManager::GetStackGuarantee</span><span class="sxs-lookup"><span data-stu-id="7f31f-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="7f31f-103">Obtém a quantidade de espaço de pilha que tem garantia de disponibilidade após a conclusão de uma operação de pilha, mas antes do fechamento de um processo.</span><span class="sxs-lookup"><span data-stu-id="7f31f-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f31f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f31f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f31f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7f31f-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="7f31f-106">fora Um ponteiro para o número de bytes que estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="7f31f-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f31f-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f31f-107">Requirements</span></span>  
 <span data-ttu-id="7f31f-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f31f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f31f-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7f31f-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f31f-110">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7f31f-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f31f-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f31f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f31f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f31f-112">See also</span></span>

- [<span data-ttu-id="7f31f-113">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="7f31f-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
