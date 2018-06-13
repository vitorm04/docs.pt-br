---
title: Método IMetaDataImport2::EnumGenericParamConstraints
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd5d35cb13bb55fc73e160089cbc1050cb3d5c0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449212"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="de8aa-102">Método IMetaDataImport2::EnumGenericParamConstraints</span><span class="sxs-lookup"><span data-stu-id="de8aa-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="de8aa-103">Obtém um enumerador para uma matriz de restrições de parâmetro genérico associadas com o parâmetro genérico representado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="de8aa-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de8aa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de8aa-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de8aa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="de8aa-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="de8aa-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="de8aa-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="de8aa-107">[in]   Um token que representa o parâmetro genérico cujas restrições devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="de8aa-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="de8aa-108">[out] A matriz de restrições de parâmetro genérico para enumerar.</span><span class="sxs-lookup"><span data-stu-id="de8aa-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="de8aa-109">[in]   O número máximo solicitado de tokens para colocar em `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="de8aa-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="de8aa-110">[out] Um ponteiro para o número de tokens são colocados em `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="de8aa-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de8aa-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="de8aa-111">Return Value</span></span>  
  
|<span data-ttu-id="de8aa-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="de8aa-112">HRESULT</span></span>|<span data-ttu-id="de8aa-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="de8aa-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="de8aa-114">`EnumGenericParameterConstraints` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="de8aa-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="de8aa-115">`phEnum` não tem nenhum elemento de membro.</span><span class="sxs-lookup"><span data-stu-id="de8aa-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="de8aa-116">Nesse caso, `pcGenericParameterConstraints` é definido como 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="de8aa-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="de8aa-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="de8aa-117">Requirements</span></span>  
 <span data-ttu-id="de8aa-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de8aa-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de8aa-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="de8aa-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de8aa-120">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="de8aa-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="de8aa-121">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de8aa-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de8aa-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de8aa-122">See Also</span></span>  
 [<span data-ttu-id="de8aa-123">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="de8aa-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="de8aa-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="de8aa-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
