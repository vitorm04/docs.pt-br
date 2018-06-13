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
ms.openlocfilehash: 6b699539df52bda9206191dd89c0f95de69140a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443880"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="42e53-102">Método IMetaDataEmit::SetCustomAttributeValue</span><span class="sxs-lookup"><span data-stu-id="42e53-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="42e53-103">Define ou atualiza o valor de um atributo personalizado definido por uma chamada anterior ao [Definecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="42e53-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42e53-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42e53-104">Syntax</span></span>  
  
```  
HRESULT SetCustomAttributeValue (   
    [in]  mdCustomAttribute       pcv,   
    [in]  void const              *pCustomAttribute,    
    [in]  ULONG                   cbCustomAttribute   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42e53-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="42e53-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="42e53-106">[in] O token do atributo personalizado de destino.</span><span class="sxs-lookup"><span data-stu-id="42e53-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="42e53-107">[in] Um ponteiro para a matriz que contém o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="42e53-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="42e53-108">[in] O tamanho, em bytes, do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="42e53-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42e53-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="42e53-109">Requirements</span></span>  
 <span data-ttu-id="42e53-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42e53-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42e53-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="42e53-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="42e53-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="42e53-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42e53-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42e53-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42e53-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42e53-114">See Also</span></span>  
 [<span data-ttu-id="42e53-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="42e53-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="42e53-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="42e53-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
