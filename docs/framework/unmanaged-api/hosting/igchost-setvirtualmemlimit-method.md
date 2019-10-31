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
ms.openlocfilehash: c060e4883335a8318970b5fbd74bf72c9e13f5bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134870"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="28954-102">Método IGCHost::SetVirtualMemLimit</span><span class="sxs-lookup"><span data-stu-id="28954-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="28954-103">Define o tamanho máximo da memória virtual do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="28954-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28954-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28954-104">Syntax</span></span>  
  
```cpp  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28954-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="28954-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="28954-106">no O tamanho máximo, em megabytes, da memória virtual do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="28954-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28954-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="28954-107">Remarks</span></span>  
 <span data-ttu-id="28954-108">O tamanho máximo da memória virtual do tempo de execução pode ser alterado dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="28954-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28954-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28954-109">Requirements</span></span>  
 <span data-ttu-id="28954-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28954-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28954-111">**Cabeçalho:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="28954-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="28954-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="28954-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28954-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28954-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28954-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28954-114">See also</span></span>

- [<span data-ttu-id="28954-115">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="28954-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
