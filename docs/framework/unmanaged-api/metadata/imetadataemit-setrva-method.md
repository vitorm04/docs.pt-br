---
title: Método IMetaDataEmit::SetRVA
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetRVA
helpviewer_keywords:
- IMetaDataEmit::SetRVA method [.NET Framework metadata]
- SetRVA method [.NET Framework metadata]
ms.assetid: 4d69fb6d-ee35-4318-8224-5eea2bd16818
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1a9df30ae11b13c052c75b05b0850d9f4754620
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470088"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="177b7-102">Método IMetaDataEmit::SetRVA</span><span class="sxs-lookup"><span data-stu-id="177b7-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="177b7-103">Define o endereço virtual relativo do método especificado.</span><span class="sxs-lookup"><span data-stu-id="177b7-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="177b7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="177b7-104">Syntax</span></span>  
  
```  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,   
    [in]  ULONG        ulRVA   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="177b7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="177b7-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="177b7-106">[in] O token para o método de destino ou a implementação do método.</span><span class="sxs-lookup"><span data-stu-id="177b7-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="177b7-107">[in] O endereço da área do código ou dados.</span><span class="sxs-lookup"><span data-stu-id="177b7-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="177b7-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="177b7-108">Requirements</span></span>  
 <span data-ttu-id="177b7-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="177b7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="177b7-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="177b7-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="177b7-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="177b7-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="177b7-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="177b7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="177b7-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="177b7-113">See also</span></span>
- [<span data-ttu-id="177b7-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="177b7-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="177b7-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="177b7-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
