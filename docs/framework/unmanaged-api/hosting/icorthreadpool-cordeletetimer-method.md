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
ms.openlocfilehash: 098c23dd0ddff4342aa4cefbaa4e149ed95a1cb3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178341"
---
# <a name="icorthreadpoolcordeletetimer-method"></a><span data-ttu-id="fbfc6-102">Método ICorThreadpool::CorDeleteTimer</span><span class="sxs-lookup"><span data-stu-id="fbfc6-102">ICorThreadpool::CorDeleteTimer Method</span></span>
<span data-ttu-id="fbfc6-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="fbfc6-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbfc6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbfc6-104">Syntax</span></span>  
  
```  
HRESULT CorDeleteTimer (  
    [in]  HANDLE Timer,  
    [in]  HANDLE CompletionEvent,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="fbfc6-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fbfc6-105">Requirements</span></span>  
 <span data-ttu-id="fbfc6-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbfc6-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbfc6-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fbfc6-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fbfc6-108">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="fbfc6-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="fbfc6-109">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="fbfc6-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fbfc6-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbfc6-110">See also</span></span>

- [<span data-ttu-id="fbfc6-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="fbfc6-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
