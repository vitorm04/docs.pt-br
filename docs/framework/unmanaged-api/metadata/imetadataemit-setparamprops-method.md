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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8448de17ad974bc77021a7880b7d8576c69ae75
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750918"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="8f90e-102">Método IMetaDataEmit::SetParamProps</span><span class="sxs-lookup"><span data-stu-id="8f90e-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="8f90e-103">Define ou altera os recursos de um parâmetro de método que foi definido por uma chamada anterior ao [imetadataemit:: Defineparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="8f90e-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f90e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f90e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8f90e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8f90e-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="8f90e-106">[in] O token para o parâmetro de destino.</span><span class="sxs-lookup"><span data-stu-id="8f90e-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="8f90e-107">[in] O nome do parâmetro no Unicode.</span><span class="sxs-lookup"><span data-stu-id="8f90e-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="8f90e-108">[in] Os sinalizadores para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8f90e-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="8f90e-109">[in] O ELEMENT_TYPE _ \* para o valor da constante.</span><span class="sxs-lookup"><span data-stu-id="8f90e-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="8f90e-110">[in] O valor da constante para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8f90e-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="8f90e-111">[in] O tamanho em caracteres (Unicode) do `pValue`.</span><span class="sxs-lookup"><span data-stu-id="8f90e-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f90e-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8f90e-112">Requirements</span></span>  
 <span data-ttu-id="8f90e-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f90e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f90e-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8f90e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8f90e-115">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8f90e-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f90e-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f90e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f90e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f90e-117">See also</span></span>

- [<span data-ttu-id="8f90e-118">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="8f90e-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="8f90e-119">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="8f90e-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
