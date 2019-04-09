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
ms.openlocfilehash: e17a6846ba0276ec7ba423ab25e3f11baf278d03
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098748"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="0c65c-102">Método IMetaDataEmit::SetRVA</span><span class="sxs-lookup"><span data-stu-id="0c65c-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="0c65c-103">Define o endereço virtual relativo do método especificado.</span><span class="sxs-lookup"><span data-stu-id="0c65c-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c65c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c65c-104">Syntax</span></span>  
  
```  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,   
    [in]  ULONG        ulRVA   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c65c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0c65c-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="0c65c-106">[in] O token para o método de destino ou a implementação do método.</span><span class="sxs-lookup"><span data-stu-id="0c65c-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="0c65c-107">[in] O endereço da área do código ou dados.</span><span class="sxs-lookup"><span data-stu-id="0c65c-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c65c-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0c65c-108">Requirements</span></span>  
 <span data-ttu-id="0c65c-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c65c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c65c-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0c65c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0c65c-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0c65c-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="0c65c-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="0c65c-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0c65c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c65c-113">See also</span></span>

- [<span data-ttu-id="0c65c-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="0c65c-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0c65c-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="0c65c-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
