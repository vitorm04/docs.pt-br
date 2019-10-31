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
ms.openlocfilehash: be488ebe663169cabc5b569335dfc784fdf30556
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102687"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="633e1-102">Método IObjectHandle::Unwrap</span><span class="sxs-lookup"><span data-stu-id="633e1-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="633e1-103">Desenvolve um objeto Marshal-by-Value de indireção.</span><span class="sxs-lookup"><span data-stu-id="633e1-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="633e1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="633e1-104">Syntax</span></span>  
  
```cpp  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="633e1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="633e1-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="633e1-106">fora Um ponteiro para o objeto a ser desencapsulado.</span><span class="sxs-lookup"><span data-stu-id="633e1-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="633e1-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="633e1-107">Requirements</span></span>  
 <span data-ttu-id="633e1-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="633e1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="633e1-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="633e1-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="633e1-110">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="633e1-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="633e1-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="633e1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
