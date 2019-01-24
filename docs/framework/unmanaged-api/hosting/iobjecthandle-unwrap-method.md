---
title: Método IObjectHandle::Unwrap
ms.date: 03/30/2017
api_name:
- IObjectHandle.Unwrap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Unwrap
helpviewer_keywords:
- Unwrap method [.NET Framework hosting]
- IObjectHandle::Unwrap method [.NET Framework hosting]
ms.assetid: 794c6f8e-ed58-416b-b756-e864f2c958f7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da25055917743481f5a8314023ed94d552fe49ce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526412"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="2e2e6-102">Método IObjectHandle::Unwrap</span><span class="sxs-lookup"><span data-stu-id="2e2e6-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="2e2e6-103">Desencapsula um objeto de marshaling por valor de uma indireção.</span><span class="sxs-lookup"><span data-stu-id="2e2e6-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e2e6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e2e6-104">Syntax</span></span>  
  
```  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e2e6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2e2e6-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="2e2e6-106">[out] Um ponteiro para o objeto a ser descodificada.</span><span class="sxs-lookup"><span data-stu-id="2e2e6-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e2e6-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e2e6-107">Requirements</span></span>  
 <span data-ttu-id="2e2e6-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e2e6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e2e6-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2e2e6-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e2e6-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="2e2e6-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e2e6-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e2e6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e2e6-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e2e6-112">See also</span></span>

