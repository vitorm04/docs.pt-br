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
ms.openlocfilehash: ac76a9af6839ea08169c8b9c143fa96066e954ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="b6337-102">Método IMetaDataEmit::SetParamProps</span><span class="sxs-lookup"><span data-stu-id="b6337-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="b6337-103">Define ou altera os recursos de um parâmetro de método definido por uma chamada anterior ao [: Defineparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="b6337-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6337-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6337-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="b6337-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b6337-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="b6337-106">[in] O token para o parâmetro de destino.</span><span class="sxs-lookup"><span data-stu-id="b6337-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="b6337-107">[in] O nome do parâmetro em Unicode.</span><span class="sxs-lookup"><span data-stu-id="b6337-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="b6337-108">[in] Os sinalizadores para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b6337-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="b6337-109">[in] O ELEMENT_TYPE _ * para o valor da constante.</span><span class="sxs-lookup"><span data-stu-id="b6337-109">[in] The ELEMENT_TYPE_* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="b6337-110">[in] O valor da constante para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b6337-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="b6337-111">[in] O tamanho em caracteres (Unicode) do `pValue`.</span><span class="sxs-lookup"><span data-stu-id="b6337-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6337-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b6337-112">Requirements</span></span>  
 <span data-ttu-id="b6337-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6337-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6337-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b6337-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6337-115">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b6337-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6337-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6337-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6337-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6337-117">See Also</span></span>  
 [<span data-ttu-id="b6337-118">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b6337-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="b6337-119">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b6337-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
