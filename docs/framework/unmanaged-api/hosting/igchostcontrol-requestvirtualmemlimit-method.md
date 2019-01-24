---
title: Método IGCHostControl::RequestVirtualMemLimit
ms.date: 03/30/2017
api_name:
- IGCHostControl.RequestVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db1572c035242a4a143ee435957409e5d16fca1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607167"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="320d0-102">Método IGCHostControl::RequestVirtualMemLimit</span><span class="sxs-lookup"><span data-stu-id="320d0-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="320d0-103">Solicitações de host para alterar os limites de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="320d0-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="320d0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="320d0-104">Syntax</span></span>  
  
```  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="320d0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="320d0-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="320d0-106">[in] O tamanho solicitado da alocação de memória.</span><span class="sxs-lookup"><span data-stu-id="320d0-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="320d0-107">[no, out] Um ponteiro para o tamanho real da memória alocada.</span><span class="sxs-lookup"><span data-stu-id="320d0-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="320d0-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="320d0-108">Requirements</span></span>  
 <span data-ttu-id="320d0-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="320d0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="320d0-110">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="320d0-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="320d0-111">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="320d0-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="320d0-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="320d0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="320d0-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="320d0-113">See also</span></span>
- [<span data-ttu-id="320d0-114">Interface IGCHostControl</span><span class="sxs-lookup"><span data-stu-id="320d0-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
