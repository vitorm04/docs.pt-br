---
title: "Função GetIdentityAuthority"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetIdentityAuthority
api_location:
- fusion.dll
- clr.dll
api_type: COM
f1_keywords: GetIdentityAuthority
helpviewer_keywords: GetIdentityAuthority function [.NET Framework fusion]
ms.assetid: 843cd5ab-d2b7-4ff6-86bd-e68c7a91c098
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1490efdc00c4f928d17bf172eecd5a3bed824193
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="7b8f7-102">Função GetIdentityAuthority</span><span class="sxs-lookup"><span data-stu-id="7b8f7-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="7b8f7-103">Obtém um ponteiro para um [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instância que gerencia chaves para objetos de código.</span><span class="sxs-lookup"><span data-stu-id="7b8f7-103">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b8f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b8f7-104">Syntax</span></span>  
  
```  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b8f7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7b8f7-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="7b8f7-106">[out] Retornado `IIdentityAuthority` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="7b8f7-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b8f7-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b8f7-107">Requirements</span></span>  
 <span data-ttu-id="7b8f7-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b8f7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b8f7-109">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="7b8f7-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="7b8f7-110">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b8f7-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b8f7-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b8f7-111">See Also</span></span>  
 [<span data-ttu-id="7b8f7-112">Interface IIdentityAuthority</span><span class="sxs-lookup"><span data-stu-id="7b8f7-112">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)  
 [<span data-ttu-id="7b8f7-113">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="7b8f7-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
