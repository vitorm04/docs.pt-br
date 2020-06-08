---
title: Método IMetaDataFilter::MarkToken
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type:
- apiref
ms.openlocfilehash: 28a5f79f6fa8d25fd254c4093b0f76e0308edbad
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492519"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="42524-102">Método IMetaDataFilter::MarkToken</span><span class="sxs-lookup"><span data-stu-id="42524-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="42524-103">Define um valor que indica que o token de metadados especificado foi processado.</span><span class="sxs-lookup"><span data-stu-id="42524-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42524-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42524-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42524-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="42524-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="42524-106">no O token a ser marcado como processado.</span><span class="sxs-lookup"><span data-stu-id="42524-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42524-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="42524-107">Requirements</span></span>  
 <span data-ttu-id="42524-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42524-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42524-109">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="42524-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="42524-110">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="42524-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="42524-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42524-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42524-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="42524-112">See also</span></span>

- [<span data-ttu-id="42524-113">Interface IMetaDataFilter</span><span class="sxs-lookup"><span data-stu-id="42524-113">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
