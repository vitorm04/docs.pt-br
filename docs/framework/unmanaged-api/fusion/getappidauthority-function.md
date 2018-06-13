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
ms.openlocfilehash: 419884cfd4cbcbcdaa999c221b56ee9873a90241
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429102"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="f1402-102">Função GetAppIdAuthority</span><span class="sxs-lookup"><span data-stu-id="f1402-102">GetAppIdAuthority Function</span></span>
<span data-ttu-id="f1402-103">Obtém um ponteiro para um [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instância que gerencia chaves de identidades de aplicativo e referências.</span><span class="sxs-lookup"><span data-stu-id="f1402-103">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1402-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1402-104">Syntax</span></span>  
  
```  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1402-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f1402-105">Parameters</span></span>  
 `ppIAppIdAuthority`  
 <span data-ttu-id="f1402-106">[out] Retornado `IAppIdAuthority` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="f1402-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1402-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1402-107">Requirements</span></span>  
 <span data-ttu-id="f1402-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1402-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1402-109">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="f1402-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="f1402-110">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1402-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1402-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1402-111">See Also</span></span>  
 [<span data-ttu-id="f1402-112">Interface IAppIdAuthority</span><span class="sxs-lookup"><span data-stu-id="f1402-112">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 [<span data-ttu-id="f1402-113">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="f1402-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
