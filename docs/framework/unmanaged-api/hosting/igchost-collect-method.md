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
ms.openlocfilehash: e20ea6addc1ae3f99b4b3d65f532e0128ac160b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134968"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="e01f3-102">Método IGCHost::Collect</span><span class="sxs-lookup"><span data-stu-id="e01f3-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="e01f3-103">Força a ocorrência de uma coleção para a geração determinada, independentemente do estado da coleta de lixo atual.</span><span class="sxs-lookup"><span data-stu-id="e01f3-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e01f3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e01f3-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e01f3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e01f3-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="e01f3-106">no A geração na qual executar a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e01f3-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="e01f3-107">Um valor de-1 indica que todas as gerações passarão por uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e01f3-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e01f3-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e01f3-108">Requirements</span></span>  
 <span data-ttu-id="e01f3-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e01f3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e01f3-110">**Cabeçalho:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="e01f3-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="e01f3-111">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e01f3-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e01f3-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e01f3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e01f3-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e01f3-113">See also</span></span>

- [<span data-ttu-id="e01f3-114">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="e01f3-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
