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
ms.openlocfilehash: fd5e71071de9e6afebc8f1848e0af8835f22c9bf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448130"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="4f9e9-102">Método IMetaDataEmit::SetCustomAttributeValue</span><span class="sxs-lookup"><span data-stu-id="4f9e9-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="4f9e9-103">Define ou atualiza o valor de um atributo personalizado definido por uma chamada anterior para [IMetaDataEmit::D efinecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="4f9e9-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f9e9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f9e9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (   
    [in]  mdCustomAttribute       pcv,   
    [in]  void const              *pCustomAttribute,    
    [in]  ULONG                   cbCustomAttribute   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f9e9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4f9e9-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="4f9e9-106">no O token do atributo personalizado de destino.</span><span class="sxs-lookup"><span data-stu-id="4f9e9-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="4f9e9-107">no Um ponteiro para a matriz que contém o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="4f9e9-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="4f9e9-108">no O tamanho, em bytes, do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="4f9e9-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f9e9-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4f9e9-109">Requirements</span></span>  
 <span data-ttu-id="4f9e9-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f9e9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f9e9-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4f9e9-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f9e9-112">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4f9e9-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f9e9-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f9e9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f9e9-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f9e9-114">See also</span></span>

- [<span data-ttu-id="4f9e9-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="4f9e9-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4f9e9-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="4f9e9-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
