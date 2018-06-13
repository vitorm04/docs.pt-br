---
title: Método IGCHost::SetVirtualMemLimit
ms.date: 03/30/2017
api_name:
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1d61c8aeaf458d8cbbd2976fa83aaa0eeb0f834
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437733"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="31d5f-102">Método IGCHost::SetVirtualMemLimit</span><span class="sxs-lookup"><span data-stu-id="31d5f-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="31d5f-103">Define o tamanho máximo de memória virtual do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="31d5f-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31d5f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31d5f-104">Syntax</span></span>  
  
```  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31d5f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="31d5f-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="31d5f-106">[in] O tamanho máximo, em megabytes, da memória virtual do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="31d5f-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31d5f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="31d5f-107">Remarks</span></span>  
 <span data-ttu-id="31d5f-108">O tamanho máximo de memória virtual do tempo de execução pode ser alterado dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="31d5f-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31d5f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31d5f-109">Requirements</span></span>  
 <span data-ttu-id="31d5f-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31d5f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31d5f-111">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="31d5f-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="31d5f-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="31d5f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31d5f-113">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31d5f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d5f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31d5f-114">See Also</span></span>  
 [<span data-ttu-id="31d5f-115">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="31d5f-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
