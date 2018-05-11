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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5bf5149e8e42a810a6a490767638b374f66b5679
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="d1389-102">Método IMetaDataFilter::IsTokenMarked</span><span class="sxs-lookup"><span data-stu-id="d1389-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="d1389-103">Obtém um valor que indica se o token de metadados especificado foi marcado como processada.</span><span class="sxs-lookup"><span data-stu-id="d1389-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1389-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1389-104">Syntax</span></span>  
  
```  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,   
    [out] BOOL     *pIsMarked  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1389-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d1389-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="d1389-106">[in] O token para examinar por uma marca de processamento.</span><span class="sxs-lookup"><span data-stu-id="d1389-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="d1389-107">[out] Um valor que é `true` se `tk` foi processado; caso contrário `false`.</span><span class="sxs-lookup"><span data-stu-id="d1389-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1389-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d1389-108">Requirements</span></span>  
 <span data-ttu-id="d1389-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1389-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1389-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d1389-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1389-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d1389-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d1389-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1389-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1389-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1389-113">See Also</span></span>  
 [<span data-ttu-id="d1389-114">Interface IMetaDataFilter</span><span class="sxs-lookup"><span data-stu-id="d1389-114">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
