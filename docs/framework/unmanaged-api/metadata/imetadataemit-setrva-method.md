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
ms.openlocfilehash: 89475ebc5ef04c8693adb7a83bd1dd07f5774fb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544686"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="8a939-102">Método IMetaDataEmit::SetRVA</span><span class="sxs-lookup"><span data-stu-id="8a939-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="8a939-103">Define o endereço virtual relativo do método especificado.</span><span class="sxs-lookup"><span data-stu-id="8a939-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a939-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a939-104">Syntax</span></span>  
  
```  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,   
    [in]  ULONG        ulRVA   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a939-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8a939-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="8a939-106">[in] O token para o método de destino ou a implementação do método.</span><span class="sxs-lookup"><span data-stu-id="8a939-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="8a939-107">[in] O endereço da área do código ou dados.</span><span class="sxs-lookup"><span data-stu-id="8a939-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a939-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a939-108">Requirements</span></span>  
 <span data-ttu-id="8a939-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a939-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a939-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8a939-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a939-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8a939-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a939-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a939-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a939-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a939-113">See also</span></span>
- [<span data-ttu-id="8a939-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="8a939-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="8a939-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="8a939-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
