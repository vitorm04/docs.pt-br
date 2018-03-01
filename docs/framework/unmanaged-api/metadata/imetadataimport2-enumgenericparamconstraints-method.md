---
title: "Método IMetaDataImport2::EnumGenericParamConstraints"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport2.EnumGenericParamConstraints
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 72f863205c0fa7f4c6b4477c9d9143d1923a5d4c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="716f6-102">Método IMetaDataImport2::EnumGenericParamConstraints</span><span class="sxs-lookup"><span data-stu-id="716f6-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="716f6-103">Obtém um enumerador para uma matriz de restrições de parâmetro genérico associadas com o parâmetro genérico representado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="716f6-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="716f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="716f6-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="716f6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="716f6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="716f6-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="716f6-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="716f6-107">[in]   Um token que representa o parâmetro genérico cujas restrições devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="716f6-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="716f6-108">[out] A matriz de restrições de parâmetro genérico para enumerar.</span><span class="sxs-lookup"><span data-stu-id="716f6-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="716f6-109">[in]   O número máximo solicitado de tokens para colocar em `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="716f6-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="716f6-110">[out] Um ponteiro para o número de tokens são colocados em `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="716f6-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="716f6-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="716f6-111">Return Value</span></span>  
  
|<span data-ttu-id="716f6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="716f6-112">HRESULT</span></span>|<span data-ttu-id="716f6-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="716f6-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="716f6-114">`EnumGenericParameterConstraints`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="716f6-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="716f6-115">`phEnum`não tem nenhum elemento de membro.</span><span class="sxs-lookup"><span data-stu-id="716f6-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="716f6-116">Nesse caso, `pcGenericParameterConstraints` é definido como 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="716f6-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="716f6-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="716f6-117">Requirements</span></span>  
 <span data-ttu-id="716f6-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="716f6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="716f6-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="716f6-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="716f6-120">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="716f6-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="716f6-121">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="716f6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="716f6-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="716f6-122">See Also</span></span>  
 [<span data-ttu-id="716f6-123">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="716f6-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="716f6-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="716f6-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
