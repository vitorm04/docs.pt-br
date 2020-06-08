---
title: Método IMetaDataFilter::IsTokenMarked
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.IsTokenMarked
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::IsTokenMarked
helpviewer_keywords:
- IMetaDataFilter::IsTokenMarked method [.NET Framework metadata]
- IsTokenMarked method [.NET Framework metadata]
ms.assetid: 7d90dcee-0206-4540-807b-06982fe65f1a
topic_type:
- apiref
ms.openlocfilehash: eb0ebab0f4e05d81730d5beb2b5345e319e8e274
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492532"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="bdd0a-102">Método IMetaDataFilter::IsTokenMarked</span><span class="sxs-lookup"><span data-stu-id="bdd0a-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="bdd0a-103">Obtém um valor que indica se o token de metadados especificado foi marcado como processado.</span><span class="sxs-lookup"><span data-stu-id="bdd0a-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdd0a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bdd0a-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdd0a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bdd0a-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="bdd0a-106">no O token para examinar uma marca de processamento.</span><span class="sxs-lookup"><span data-stu-id="bdd0a-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="bdd0a-107">fora Um valor que `true` se foi `tk` processado; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="bdd0a-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdd0a-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bdd0a-108">Requirements</span></span>  
 <span data-ttu-id="bdd0a-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdd0a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdd0a-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bdd0a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bdd0a-111">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bdd0a-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bdd0a-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdd0a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd0a-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="bdd0a-113">See also</span></span>

- [<span data-ttu-id="bdd0a-114">Interface IMetaDataFilter</span><span class="sxs-lookup"><span data-stu-id="bdd0a-114">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
