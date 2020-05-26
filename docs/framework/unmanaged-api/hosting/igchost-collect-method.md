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
ms.openlocfilehash: ac73c462aa210927f0665cae161fd7f3e17a0cdb
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805306"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="9918e-102">Método IGCHost::Collect</span><span class="sxs-lookup"><span data-stu-id="9918e-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="9918e-103">Força a ocorrência de uma coleção para a geração determinada, independentemente do estado da coleta de lixo atual.</span><span class="sxs-lookup"><span data-stu-id="9918e-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9918e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9918e-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9918e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9918e-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="9918e-106">no A geração na qual executar a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9918e-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="9918e-107">Um valor de-1 indica que todas as gerações passarão por uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9918e-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9918e-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9918e-108">Requirements</span></span>  
 <span data-ttu-id="9918e-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9918e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9918e-110">**Cabeçalho:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="9918e-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="9918e-111">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9918e-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9918e-112">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9918e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9918e-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="9918e-113">See also</span></span>

- [<span data-ttu-id="9918e-114">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="9918e-114">IGCHost Interface</span></span>](igchost-interface.md)
