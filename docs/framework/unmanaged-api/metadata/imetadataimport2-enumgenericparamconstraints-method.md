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
ms.openlocfilehash: d1683965193801dbdee038ab06366178891fd978
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426730"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="6e5fa-102">Método IMetaDataImport2::EnumGenericParamConstraints</span><span class="sxs-lookup"><span data-stu-id="6e5fa-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="6e5fa-103">Obtém um enumerador para uma matriz de restrições de parâmetro genérico associadas ao parâmetro genérico representado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="6e5fa-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e5fa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e5fa-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e5fa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e5fa-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6e5fa-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="6e5fa-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="6e5fa-107">no   Um token que representa o parâmetro genérico cujas restrições devem ser enumeradas.</span><span class="sxs-lookup"><span data-stu-id="6e5fa-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="6e5fa-108">fora A matriz de restrições de parâmetro genérico para enumerar.</span><span class="sxs-lookup"><span data-stu-id="6e5fa-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6e5fa-109">no   O número máximo solicitado de tokens a serem colocados no `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="6e5fa-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="6e5fa-110">fora Um ponteiro para o número de tokens colocados em `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="6e5fa-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e5fa-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="6e5fa-111">Return Value</span></span>  
  
|<span data-ttu-id="6e5fa-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6e5fa-112">HRESULT</span></span>|<span data-ttu-id="6e5fa-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e5fa-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6e5fa-114">`EnumGenericParameterConstraints` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="6e5fa-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6e5fa-115">`phEnum` não tem elementos de membro.</span><span class="sxs-lookup"><span data-stu-id="6e5fa-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="6e5fa-116">Nesse caso, `pcGenericParameterConstraints` é definido como 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="6e5fa-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6e5fa-117">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="6e5fa-117">Requirements</span></span>  
 <span data-ttu-id="6e5fa-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e5fa-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e5fa-119">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6e5fa-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e5fa-120">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6e5fa-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6e5fa-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e5fa-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e5fa-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e5fa-122">See also</span></span>

- [<span data-ttu-id="6e5fa-123">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="6e5fa-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="6e5fa-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="6e5fa-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
