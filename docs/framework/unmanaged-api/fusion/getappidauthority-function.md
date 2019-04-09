---
title: Função GetAppIdAuthority
ms.date: 03/30/2017
api_name:
- GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetAppIdAuthority
helpviewer_keywords:
- GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 274b91793cd51348c42661bf12a4e4385e17f630
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093963"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="b5f16-102">Função GetAppIdAuthority</span><span class="sxs-lookup"><span data-stu-id="b5f16-102">GetAppIdAuthority Function</span></span>
<span data-ttu-id="b5f16-103">Obtém um ponteiro para um [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instância que gerencia as chaves para as identidades de aplicativo e referências.</span><span class="sxs-lookup"><span data-stu-id="b5f16-103">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5f16-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5f16-104">Syntax</span></span>  
  
```  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5f16-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b5f16-105">Parameters</span></span>  
 `ppIAppIdAuthority`  
 <span data-ttu-id="b5f16-106">[out] Retornado `IAppIdAuthority` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="b5f16-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5f16-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5f16-107">Requirements</span></span>  
 <span data-ttu-id="b5f16-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5f16-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5f16-109">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="b5f16-109">**Header:** Isolation.h</span></span>  
  
 **<span data-ttu-id="b5f16-110">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b5f16-110">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b5f16-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5f16-111">See also</span></span>

- [<span data-ttu-id="b5f16-112">Interface IAppIdAuthority</span><span class="sxs-lookup"><span data-stu-id="b5f16-112">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)
- [<span data-ttu-id="b5f16-113">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="b5f16-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
