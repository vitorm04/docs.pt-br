---
title: Método IMetaDataEmit::SetCustomAttributeValue
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetCustomAttributeValue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetCustomAttributeValue
helpviewer_keywords:
- SetCustomAttributeValue method [.NET Framework metadata]
- IMetaDataEmit::SetCustomAttributeValue method [.NET Framework metadata]
ms.assetid: f721c863-9642-4e64-917a-65f9e55c25b9
topic_type:
- apiref
ms.openlocfilehash: 25b7f478ae0bd05b82fa960561fb8534efe2b4db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175662"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="71d59-102">Método IMetaDataEmit::SetCustomAttributeValue</span><span class="sxs-lookup"><span data-stu-id="71d59-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="71d59-103">Define ou atualiza o valor de um atributo personalizado definido por uma chamada anterior ao [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="71d59-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71d59-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71d59-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (
    [in]  mdCustomAttribute       pcv,
    [in]  void const              *pCustomAttribute,
    [in]  ULONG                   cbCustomAttribute
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71d59-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="71d59-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="71d59-106">[em] O símbolo do atributo personalizado do alvo.</span><span class="sxs-lookup"><span data-stu-id="71d59-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="71d59-107">[em] Um ponteiro para a matriz que contém o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="71d59-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="71d59-108">[em] O tamanho, em bytes, do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="71d59-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71d59-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="71d59-109">Requirements</span></span>  
 <span data-ttu-id="71d59-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71d59-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71d59-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="71d59-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="71d59-112">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="71d59-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71d59-113">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71d59-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d59-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="71d59-114">See also</span></span>

- [<span data-ttu-id="71d59-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="71d59-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="71d59-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="71d59-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
