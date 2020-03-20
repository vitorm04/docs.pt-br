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
ms.openlocfilehash: bb3778a55e7f395ad65f6a9841ca1f31f1de4ebc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178253"
---
# <a name="icorthreadpoolcorchangetimer-method"></a><span data-ttu-id="a62dc-102">Método ICorThreadpool::CorChangeTimer</span><span class="sxs-lookup"><span data-stu-id="a62dc-102">ICorThreadpool::CorChangeTimer Method</span></span>
<span data-ttu-id="a62dc-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="a62dc-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a62dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a62dc-104">Syntax</span></span>  
  
```cpp  
HRESULT CorChangeTimer (  
    [in]  HANDLE Timer,
    [in]  ULONG  DueTime,
    [in]  ULONG  Period,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a62dc-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a62dc-105">Requirements</span></span>  
 <span data-ttu-id="a62dc-106">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a62dc-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a62dc-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a62dc-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a62dc-108">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a62dc-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a62dc-109">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a62dc-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a62dc-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="a62dc-110">See also</span></span>

- [<span data-ttu-id="a62dc-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="a62dc-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
