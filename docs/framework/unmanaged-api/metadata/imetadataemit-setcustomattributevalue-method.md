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
ms.openlocfilehash: 6e24db7da7abbdb597b8ff64515e8053667af3ff
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008762"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="fb61f-102">Método IMetaDataEmit::SetCustomAttributeValue</span><span class="sxs-lookup"><span data-stu-id="fb61f-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="fb61f-103">Define ou atualiza o valor de um atributo personalizado definido por uma chamada anterior para [IMetaDataEmit::D efinecustomattribute](imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="fb61f-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb61f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb61f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (
    [in]  mdCustomAttribute       pcv,
    [in]  void const              *pCustomAttribute,
    [in]  ULONG                   cbCustomAttribute
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb61f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fb61f-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="fb61f-106">no O token do atributo personalizado de destino.</span><span class="sxs-lookup"><span data-stu-id="fb61f-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="fb61f-107">no Um ponteiro para a matriz que contém o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="fb61f-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="fb61f-108">no O tamanho, em bytes, do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="fb61f-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb61f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb61f-109">Requirements</span></span>  
 <span data-ttu-id="fb61f-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb61f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb61f-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fb61f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fb61f-112">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fb61f-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb61f-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb61f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb61f-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="fb61f-114">See also</span></span>

- [<span data-ttu-id="fb61f-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="fb61f-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="fb61f-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="fb61f-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
