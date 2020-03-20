---
title: Método IMetaDataEmit::SetParamProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
ms.openlocfilehash: 13220dcfdd260688494d5aebc50f94abf8a82215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177500"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="e6f7c-102">Método IMetaDataEmit::SetParamProps</span><span class="sxs-lookup"><span data-stu-id="e6f7c-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="e6f7c-103">Define ou altera características de um parâmetro de método definido por uma chamada anterior ao [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="e6f7c-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6f7c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6f7c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParamProps (
    [in]  mdParamDef  pd,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6f7c-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="e6f7c-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="e6f7c-106">[em] O símbolo do parâmetro alvo.</span><span class="sxs-lookup"><span data-stu-id="e6f7c-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="e6f7c-107">[em] O nome do parâmetro em Unicode.</span><span class="sxs-lookup"><span data-stu-id="e6f7c-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="e6f7c-108">[em] As bandeiras para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e6f7c-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="e6f7c-109">[em] O ELEMENT_TYPE_\* pelo valor constante.</span><span class="sxs-lookup"><span data-stu-id="e6f7c-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="e6f7c-110">[em] O valor constante para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e6f7c-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="e6f7c-111">[em] O tamanho nos caracteres `pValue`(Unicode) de .</span><span class="sxs-lookup"><span data-stu-id="e6f7c-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6f7c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6f7c-112">Requirements</span></span>  
 <span data-ttu-id="e6f7c-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6f7c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6f7c-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e6f7c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e6f7c-115">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e6f7c-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6f7c-116">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6f7c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6f7c-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="e6f7c-117">See also</span></span>

- [<span data-ttu-id="e6f7c-118">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="e6f7c-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e6f7c-119">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="e6f7c-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
