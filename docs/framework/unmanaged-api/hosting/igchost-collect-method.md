---
title: Método IGCHost::Collect
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bce005a677dcb74c176a6dddfb2726f6b1fd0e8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="igchostcollect-method"></a><span data-ttu-id="60d91-102">Método IGCHost::Collect</span><span class="sxs-lookup"><span data-stu-id="60d91-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="60d91-103">Força uma coleta ocorra para determinada geração, independentemente do estado da coleção atual de lixo.</span><span class="sxs-lookup"><span data-stu-id="60d91-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60d91-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60d91-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60d91-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="60d91-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="60d91-106">[in] A geração na qual executar a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="60d91-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="60d91-107">Um valor de -1 indica que todas as gerações passará por uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="60d91-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60d91-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="60d91-108">Requirements</span></span>  
 <span data-ttu-id="60d91-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60d91-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60d91-110">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="60d91-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="60d91-111">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="60d91-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60d91-112">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60d91-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60d91-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60d91-113">See Also</span></span>  
 [<span data-ttu-id="60d91-114">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="60d91-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
