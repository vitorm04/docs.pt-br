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
ms.openlocfilehash: 0ff088731514b2da0d8b1fa51ef48d8b71d16528
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842225"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="645c6-102">Método IObjectHandle::Unwrap</span><span class="sxs-lookup"><span data-stu-id="645c6-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="645c6-103">Desenvolve um objeto Marshal-by-Value de indireção.</span><span class="sxs-lookup"><span data-stu-id="645c6-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="645c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="645c6-104">Syntax</span></span>  
  
```cpp  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="645c6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="645c6-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="645c6-106">fora Um ponteiro para o objeto a ser desencapsulado.</span><span class="sxs-lookup"><span data-stu-id="645c6-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="645c6-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="645c6-107">Requirements</span></span>  
 <span data-ttu-id="645c6-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="645c6-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="645c6-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="645c6-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="645c6-110">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="645c6-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="645c6-111">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="645c6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
