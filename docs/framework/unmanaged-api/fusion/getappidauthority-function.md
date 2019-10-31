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
ms.openlocfilehash: 22a6af61251942f068676daaee2bdfa868e32a97
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134553"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="6766d-102">Função GetAppIdAuthority</span><span class="sxs-lookup"><span data-stu-id="6766d-102">GetAppIdAuthority Function</span></span>
<span data-ttu-id="6766d-103">Obtém um ponteiro para uma instância de [IAppIdAuthority](iappidauthority-interface.md) que gerencia chaves para identidades e referências de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6766d-103">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6766d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6766d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="6766d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6766d-105">Parameters</span></span>  
 `ppIAppIdAuthority`  
 <span data-ttu-id="6766d-106">fora O ponteiro de `IAppIdAuthority` retornado.</span><span class="sxs-lookup"><span data-stu-id="6766d-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6766d-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6766d-107">Requirements</span></span>  
 <span data-ttu-id="6766d-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6766d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6766d-109">**Cabeçalho:** Isolamento. h</span><span class="sxs-lookup"><span data-stu-id="6766d-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="6766d-110">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6766d-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6766d-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6766d-111">See also</span></span>

- [<span data-ttu-id="6766d-112">Interface IAppIdAuthority</span><span class="sxs-lookup"><span data-stu-id="6766d-112">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)
- [<span data-ttu-id="6766d-113">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="6766d-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
