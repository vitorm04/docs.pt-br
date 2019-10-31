---
title: Método ICorThreadpool::CorChangeTimer
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorChangeTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorChangeTimer
helpviewer_keywords:
- CorChangeTimer method [.NET Framework hosting]
- ICorThreadpool::CorChangeTimer method [.NET Framework hosting]
ms.assetid: 82b03a59-5a87-43ed-9b75-e04b256e1a46
topic_type:
- apiref
ms.openlocfilehash: 330adf6ca2445f7307671d5531ce49a9d46e0fbb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133320"
---
# <a name="icorthreadpoolcorchangetimer-method"></a><span data-ttu-id="aefe8-102">Método ICorThreadpool::CorChangeTimer</span><span class="sxs-lookup"><span data-stu-id="aefe8-102">ICorThreadpool::CorChangeTimer Method</span></span>
<span data-ttu-id="aefe8-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="aefe8-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aefe8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aefe8-104">Syntax</span></span>  
  
```cpp  
HRESULT CorChangeTimer (  
    [in]  HANDLE Timer,   
    [in]  ULONG  DueTime,   
    [in]  ULONG  Period,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="aefe8-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aefe8-105">Requirements</span></span>  
 <span data-ttu-id="aefe8-106">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aefe8-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aefe8-107">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aefe8-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aefe8-108">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aefe8-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aefe8-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aefe8-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aefe8-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aefe8-110">See also</span></span>

- [<span data-ttu-id="aefe8-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="aefe8-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
