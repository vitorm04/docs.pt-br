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
ms.openlocfilehash: 371eed84883e2816892c0a6a212a4a89a287cc58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445267"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="27f71-102">Método IMetaDataEmit::SetRVA</span><span class="sxs-lookup"><span data-stu-id="27f71-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="27f71-103">Define o endereço virtual relativo do método especificado.</span><span class="sxs-lookup"><span data-stu-id="27f71-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27f71-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27f71-104">Syntax</span></span>  
  
```  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,   
    [in]  ULONG        ulRVA   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27f71-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="27f71-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="27f71-106">[in] O token para o método de destino ou a implementação do método.</span><span class="sxs-lookup"><span data-stu-id="27f71-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="27f71-107">[in] O endereço da área de dados ou de código.</span><span class="sxs-lookup"><span data-stu-id="27f71-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27f71-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27f71-108">Requirements</span></span>  
 <span data-ttu-id="27f71-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27f71-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27f71-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="27f71-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27f71-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="27f71-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27f71-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27f71-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f71-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27f71-113">See Also</span></span>  
 [<span data-ttu-id="27f71-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="27f71-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="27f71-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="27f71-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
