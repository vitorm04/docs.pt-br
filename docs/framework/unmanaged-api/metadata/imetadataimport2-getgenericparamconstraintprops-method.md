---
title: "Método IMetaDataImport2::GetGenericParamConstraintProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetGenericParamConstraintProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetGenericParamConstraintProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps method [.NET Framework metadata]
- GetGenericParamConstraintProps method [.NET Framework metadata]
ms.assetid: c5fee4a0-b132-4e5e-8730-e586ce314b9a
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7d1e560dd511758652e1acbc262b4ddc3efdd12c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="a5d46-102">Método IMetaDataImport2::GetGenericParamConstraintProps</span><span class="sxs-lookup"><span data-stu-id="a5d46-102">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>
<span data-ttu-id="a5d46-103">Obtém os metadados associados com a restrição de parâmetro genérico representada pelo token de restrição especificada.</span><span class="sxs-lookup"><span data-stu-id="a5d46-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5d46-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5d46-104">Syntax</span></span>  
  
```  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5d46-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a5d46-105">Parameters</span></span>  
 `gpc`  
 <span data-ttu-id="a5d46-106">[in] O token para a restrição de parâmetro genérico para o qual retornar os metadados.</span><span class="sxs-lookup"><span data-stu-id="a5d46-106">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="a5d46-107">[out] Um ponteiro para o token que representa o parâmetro genérico é restrito.</span><span class="sxs-lookup"><span data-stu-id="a5d46-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="a5d46-108">[out] Um ponteiro para um token de TypeDef, TypeRef ou TypeSpec que representa uma restrição em `ptGenericParam`.</span><span class="sxs-lookup"><span data-stu-id="a5d46-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5d46-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a5d46-109">Requirements</span></span>  
 <span data-ttu-id="a5d46-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5d46-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5d46-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a5d46-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a5d46-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a5d46-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a5d46-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5d46-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5d46-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5d46-114">See Also</span></span>  
 [<span data-ttu-id="a5d46-115">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="a5d46-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="a5d46-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="a5d46-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
