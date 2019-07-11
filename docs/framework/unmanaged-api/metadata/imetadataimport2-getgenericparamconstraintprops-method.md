---
title: Método IMetaDataImport2::GetGenericParamConstraintProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamConstraintProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps method [.NET Framework metadata]
- GetGenericParamConstraintProps method [.NET Framework metadata]
ms.assetid: c5fee4a0-b132-4e5e-8730-e586ce314b9a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3868b07ff01f2d1fec79537dd478a2d005f490f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778773"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="4c7c8-102">Método IMetaDataImport2::GetGenericParamConstraintProps</span><span class="sxs-lookup"><span data-stu-id="4c7c8-102">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>
<span data-ttu-id="4c7c8-103">Obtém os metadados associados com a restrição de parâmetro genérico representada pelo token de restrição especificada.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c7c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c7c8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c7c8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4c7c8-105">Parameters</span></span>  
 `gpc`  
 <span data-ttu-id="4c7c8-106">[in] O token para a restrição de parâmetro genérico para o qual retornar os metadados.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-106">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="4c7c8-107">[out] Um ponteiro para o token que representa o parâmetro genérico que é restrito.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="4c7c8-108">[out] Um ponteiro para um token de TypeDef, TypeRef ou TypeSpec que representa uma restrição em `ptGenericParam`.</span><span class="sxs-lookup"><span data-stu-id="4c7c8-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c7c8-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4c7c8-109">Requirements</span></span>  
 <span data-ttu-id="4c7c8-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c7c8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c7c8-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4c7c8-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4c7c8-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4c7c8-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4c7c8-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c7c8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c7c8-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c7c8-114">See also</span></span>

- [<span data-ttu-id="4c7c8-115">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="4c7c8-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="4c7c8-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="4c7c8-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
