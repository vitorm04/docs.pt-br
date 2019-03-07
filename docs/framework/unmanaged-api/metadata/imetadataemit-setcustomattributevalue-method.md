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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2c6e97327497993372f17e1c352ca6a8e5b2eac9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493499"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="f2d49-102">Método IMetaDataEmit::SetCustomAttributeValue</span><span class="sxs-lookup"><span data-stu-id="f2d49-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="f2d49-103">Define ou atualiza o valor de um atributo personalizado definido por uma chamada anterior ao [imetadataemit:: Definecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="f2d49-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2d49-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2d49-104">Syntax</span></span>  
  
```  
HRESULT SetCustomAttributeValue (   
    [in]  mdCustomAttribute       pcv,   
    [in]  void const              *pCustomAttribute,    
    [in]  ULONG                   cbCustomAttribute   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2d49-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f2d49-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="f2d49-106">[in] O token do atributo personalizado de destino.</span><span class="sxs-lookup"><span data-stu-id="f2d49-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="f2d49-107">[in] Um ponteiro para a matriz que contém o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="f2d49-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="f2d49-108">[in] O tamanho, em bytes, do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="f2d49-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2d49-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2d49-109">Requirements</span></span>  
 <span data-ttu-id="f2d49-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2d49-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2d49-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f2d49-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f2d49-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f2d49-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2d49-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2d49-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2d49-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2d49-114">See also</span></span>
- [<span data-ttu-id="f2d49-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f2d49-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f2d49-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f2d49-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
