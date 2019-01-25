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
ms.openlocfilehash: 32642c4ff6193e2002c8a4c7d201b36c7601debb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582533"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="29df8-102">Método IMetaDataFilter::IsTokenMarked</span><span class="sxs-lookup"><span data-stu-id="29df8-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="29df8-103">Obtém um valor que indica se o token de metadados especificado foi marcado como processada.</span><span class="sxs-lookup"><span data-stu-id="29df8-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29df8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29df8-104">Syntax</span></span>  
  
```  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,   
    [out] BOOL     *pIsMarked  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29df8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29df8-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="29df8-106">[in] O token para examinar uma marca de processamento.</span><span class="sxs-lookup"><span data-stu-id="29df8-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="29df8-107">[out] Um valor que é `true` se `tk` tiver sido processada; caso contrário `false`.</span><span class="sxs-lookup"><span data-stu-id="29df8-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29df8-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29df8-108">Requirements</span></span>  
 <span data-ttu-id="29df8-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29df8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29df8-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="29df8-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29df8-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="29df8-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="29df8-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29df8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29df8-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29df8-113">See also</span></span>
- [<span data-ttu-id="29df8-114">Interface IMetaDataFilter</span><span class="sxs-lookup"><span data-stu-id="29df8-114">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
