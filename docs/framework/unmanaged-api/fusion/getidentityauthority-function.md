---
title: Função GetIdentityAuthority
ms.date: 03/30/2017
api_name:
- GetIdentityAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetIdentityAuthority
helpviewer_keywords:
- GetIdentityAuthority function [.NET Framework fusion]
ms.assetid: 843cd5ab-d2b7-4ff6-86bd-e68c7a91c098
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f29246bdb929c8eaf1ebce726164d5cd2269b9f1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796865"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="71e68-102">Função GetIdentityAuthority</span><span class="sxs-lookup"><span data-stu-id="71e68-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="71e68-103">Obtém um ponteiro para uma instância de [IIdentityAuthority](iidentityauthority-interface.md) que gerencia chaves para objetos de código.</span><span class="sxs-lookup"><span data-stu-id="71e68-103">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71e68-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71e68-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="71e68-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="71e68-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="71e68-106">fora O ponteiro `IIdentityAuthority` retornado.</span><span class="sxs-lookup"><span data-stu-id="71e68-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71e68-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="71e68-107">Requirements</span></span>  
 <span data-ttu-id="71e68-108">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71e68-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71e68-109">**Cabeçalho:** Isolamento. h</span><span class="sxs-lookup"><span data-stu-id="71e68-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="71e68-110">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71e68-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71e68-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71e68-111">See also</span></span>

- [<span data-ttu-id="71e68-112">Interface IIdentityAuthority</span><span class="sxs-lookup"><span data-stu-id="71e68-112">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)
- [<span data-ttu-id="71e68-113">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="71e68-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
