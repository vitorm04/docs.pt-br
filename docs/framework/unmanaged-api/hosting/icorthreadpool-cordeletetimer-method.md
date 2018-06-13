---
title: Método ICorThreadpool::CorDeleteTimer
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorDeleteTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeleteTimer
helpviewer_keywords:
- ICorThreadpool::CorDeleteTimer method [.NET Framework hosting]
- CorDeleteTimer method [.NET Framework hosting]
ms.assetid: 74847c35-7ca1-466a-b750-b25e7b03d100
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6870af271f7169d9f0ad1bff99dffe4ea4cf3a62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437216"
---
# <a name="icorthreadpoolcordeletetimer-method"></a><span data-ttu-id="9dd99-102">Método ICorThreadpool::CorDeleteTimer</span><span class="sxs-lookup"><span data-stu-id="9dd99-102">ICorThreadpool::CorDeleteTimer Method</span></span>
<span data-ttu-id="9dd99-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="9dd99-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dd99-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9dd99-104">Syntax</span></span>  
  
```  
HRESULT CorDeleteTimer (  
    [in]  HANDLE Timer,  
    [in]  HANDLE CompletionEvent,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="9dd99-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9dd99-105">Requirements</span></span>  
 <span data-ttu-id="9dd99-106">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dd99-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dd99-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9dd99-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9dd99-108">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9dd99-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9dd99-109">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dd99-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd99-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9dd99-110">See Also</span></span>  
 [<span data-ttu-id="9dd99-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="9dd99-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
