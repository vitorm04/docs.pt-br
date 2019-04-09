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
ms.openlocfilehash: b5b4210bda7d41b190f1025b62132c5df896a2a1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088386"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="34061-102">Método IGCHost::SetVirtualMemLimit</span><span class="sxs-lookup"><span data-stu-id="34061-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="34061-103">Define o tamanho máximo de memória de virtual do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="34061-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34061-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34061-104">Syntax</span></span>  
  
```  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34061-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34061-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="34061-106">[in] O tamanho máximo, em megabytes, da memória virtual do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="34061-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34061-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="34061-107">Remarks</span></span>  
 <span data-ttu-id="34061-108">O tamanho máximo de memória de virtual do tempo de execução pode ser alterado dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="34061-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34061-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34061-109">Requirements</span></span>  
 <span data-ttu-id="34061-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34061-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34061-111">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="34061-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="34061-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="34061-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="34061-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="34061-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="34061-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34061-114">See also</span></span>

- [<span data-ttu-id="34061-115">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="34061-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
