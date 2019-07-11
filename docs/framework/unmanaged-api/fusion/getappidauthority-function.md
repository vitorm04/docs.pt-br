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
ms.openlocfilehash: 536f3249593333234f7f09921007b483fb80cf79
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778593"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="3f17a-102">Função GetAppIdAuthority</span><span class="sxs-lookup"><span data-stu-id="3f17a-102">GetAppIdAuthority Function</span></span>
<span data-ttu-id="3f17a-103">Obtém um ponteiro para um [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instância que gerencia as chaves para as identidades de aplicativo e referências.</span><span class="sxs-lookup"><span data-stu-id="3f17a-103">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f17a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f17a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f17a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3f17a-105">Parameters</span></span>  
 `ppIAppIdAuthority`  
 <span data-ttu-id="3f17a-106">[out] Retornado `IAppIdAuthority` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="3f17a-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f17a-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3f17a-107">Requirements</span></span>  
 <span data-ttu-id="3f17a-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f17a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f17a-109">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="3f17a-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="3f17a-110">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f17a-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f17a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f17a-111">See also</span></span>

- [<span data-ttu-id="3f17a-112">Interface IAppIdAuthority</span><span class="sxs-lookup"><span data-stu-id="3f17a-112">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)
- [<span data-ttu-id="3f17a-113">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="3f17a-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
