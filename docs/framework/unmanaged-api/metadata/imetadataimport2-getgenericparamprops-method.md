---
title: "Método IMetaDataImport2::GetGenericParamProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetGenericParamProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 70a9669e2f47c3b56f7b50dc96ed2d3ba8314c4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="980cb-102">Método IMetaDataImport2::GetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="980cb-102">IMetaDataImport2::GetGenericParamProps Method</span></span>
<span data-ttu-id="980cb-103">Obtém os metadados associados com o parâmetro genérico representado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="980cb-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="980cb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="980cb-104">Syntax</span></span>  
  
```  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="980cb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="980cb-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="980cb-106">[in] O token que representa o parâmetro genérico para o qual retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="980cb-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="980cb-107">[out] A posição ordinal do `Type` parâmetro no método ou Construtor de pai.</span><span class="sxs-lookup"><span data-stu-id="980cb-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="980cb-108">[out] Um valor de [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeração que descreve o `Type` para o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="980cb-108">[out] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="980cb-109">[out] Um token de TypeDef ou MethodDef que representa o proprietário do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="980cb-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="980cb-110">[out] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="980cb-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="980cb-111">[out] O nome do parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="980cb-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="980cb-112">[in] O tamanho do `wzName` buffer.</span><span class="sxs-lookup"><span data-stu-id="980cb-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="980cb-113">[out] O tamanho retornado do nome, em caracteres largos.</span><span class="sxs-lookup"><span data-stu-id="980cb-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="980cb-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="980cb-114">Requirements</span></span>  
 <span data-ttu-id="980cb-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="980cb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="980cb-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="980cb-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="980cb-117">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="980cb-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="980cb-118">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="980cb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="980cb-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="980cb-119">See Also</span></span>  
 [<span data-ttu-id="980cb-120">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="980cb-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="980cb-121">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="980cb-121">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
