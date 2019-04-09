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
ms.openlocfilehash: fdacb454783cfb8f90ea5a73807f0a199e16475d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154772"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="cc93b-102">Método IGCHost::Collect</span><span class="sxs-lookup"><span data-stu-id="cc93b-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="cc93b-103">Força uma coleta ocorrer para a geração de determinado, independentemente do estado da coleta de lixo atual.</span><span class="sxs-lookup"><span data-stu-id="cc93b-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc93b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc93b-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc93b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cc93b-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="cc93b-106">[in] A geração na qual executar a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="cc93b-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="cc93b-107">Um valor de -1 indica que todas as gerações passará por uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="cc93b-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc93b-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cc93b-108">Requirements</span></span>  
 <span data-ttu-id="cc93b-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc93b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc93b-110">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="cc93b-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="cc93b-111">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="cc93b-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="cc93b-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="cc93b-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cc93b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc93b-113">See also</span></span>

- [<span data-ttu-id="cc93b-114">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="cc93b-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
