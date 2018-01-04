---
title: "Método IMetaDataEmit::SetParamProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetParamProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e8ada9deddf8528321797c1f9bd06b5b775ac4bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="7e87f-102">Método IMetaDataEmit::SetParamProps</span><span class="sxs-lookup"><span data-stu-id="7e87f-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="7e87f-103">Define ou altera os recursos de um parâmetro de método definido por uma chamada anterior ao [: Defineparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="7e87f-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e87f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e87f-104">Syntax</span></span>  
  
```  
HRESULT SetParamProps (   
    [in]  mdParamDef  pd,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e87f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7e87f-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="7e87f-106">[in] O token para o parâmetro de destino.</span><span class="sxs-lookup"><span data-stu-id="7e87f-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="7e87f-107">[in] O nome do parâmetro em Unicode.</span><span class="sxs-lookup"><span data-stu-id="7e87f-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="7e87f-108">[in] Os sinalizadores para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7e87f-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="7e87f-109">[in] O ELEMENT_TYPE _ * para o valor da constante.</span><span class="sxs-lookup"><span data-stu-id="7e87f-109">[in] The ELEMENT_TYPE_* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="7e87f-110">[in] O valor da constante para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7e87f-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="7e87f-111">[in] O tamanho em caracteres (Unicode) do `pValue`.</span><span class="sxs-lookup"><span data-stu-id="7e87f-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e87f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e87f-112">Requirements</span></span>  
 <span data-ttu-id="7e87f-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e87f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e87f-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7e87f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e87f-115">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7e87f-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e87f-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e87f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e87f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e87f-117">See Also</span></span>  
 [<span data-ttu-id="7e87f-118">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="7e87f-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="7e87f-119">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="7e87f-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
