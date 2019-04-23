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
ms.openlocfilehash: 4c18607d5373b415228846350a3dd0637ade1b45
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150794"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="65215-102">Método IObjectHandle::Unwrap</span><span class="sxs-lookup"><span data-stu-id="65215-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="65215-103">Desencapsula um objeto de marshaling por valor de uma indireção.</span><span class="sxs-lookup"><span data-stu-id="65215-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65215-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65215-104">Syntax</span></span>  
  
```  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65215-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="65215-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="65215-106">[out] Um ponteiro para o objeto a ser descodificada.</span><span class="sxs-lookup"><span data-stu-id="65215-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65215-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65215-107">Requirements</span></span>  
 <span data-ttu-id="65215-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65215-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65215-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="65215-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65215-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="65215-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65215-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65215-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
