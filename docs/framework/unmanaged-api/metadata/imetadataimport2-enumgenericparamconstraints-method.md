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
ms.openlocfilehash: 2ba9d7f8873d15a7cab2b9893feb8563dfc971b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778752"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="32e3a-102">Método IMetaDataImport2::EnumGenericParamConstraints</span><span class="sxs-lookup"><span data-stu-id="32e3a-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="32e3a-103">Obtém um enumerador para uma matriz de restrições de parâmetro genérico associado com o parâmetro genérico representado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="32e3a-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32e3a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32e3a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32e3a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="32e3a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="32e3a-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="32e3a-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="32e3a-107">[in]   Um token que representa o parâmetro genérico cujas restrições são a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="32e3a-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="32e3a-108">[out] A matriz de restrições de parâmetro genérico para enumerar.</span><span class="sxs-lookup"><span data-stu-id="32e3a-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="32e3a-109">[in]   O número máximo solicitado de tokens para colocar em `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="32e3a-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="32e3a-110">[out] Um ponteiro para o número de tokens são colocados em `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="32e3a-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32e3a-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="32e3a-111">Return Value</span></span>  
  
|<span data-ttu-id="32e3a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="32e3a-112">HRESULT</span></span>|<span data-ttu-id="32e3a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="32e3a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="32e3a-114">`EnumGenericParameterConstraints` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="32e3a-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="32e3a-115">`phEnum` não tem nenhum elemento de membro.</span><span class="sxs-lookup"><span data-stu-id="32e3a-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="32e3a-116">Nesse caso, `pcGenericParameterConstraints` é definido como 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="32e3a-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="32e3a-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="32e3a-117">Requirements</span></span>  
 <span data-ttu-id="32e3a-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32e3a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32e3a-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="32e3a-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="32e3a-120">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="32e3a-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="32e3a-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32e3a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32e3a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32e3a-122">See also</span></span>

- [<span data-ttu-id="32e3a-123">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="32e3a-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="32e3a-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="32e3a-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
