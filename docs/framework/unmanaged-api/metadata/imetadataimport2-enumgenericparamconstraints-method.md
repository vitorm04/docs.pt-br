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
ms.openlocfilehash: f66b0145dbaece7292d2ccad169a97fbb10b6d11
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186674"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="1a7fc-102">Método IMetaDataImport2::EnumGenericParamConstraints</span><span class="sxs-lookup"><span data-stu-id="1a7fc-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="1a7fc-103">Obtém um enumerador para uma matriz de restrições de parâmetro genérico associado com o parâmetro genérico representado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="1a7fc-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a7fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a7fc-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a7fc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1a7fc-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1a7fc-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="1a7fc-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="1a7fc-107">[in]   Um token que representa o parâmetro genérico cujas restrições são a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="1a7fc-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="1a7fc-108">[out] A matriz de restrições de parâmetro genérico para enumerar.</span><span class="sxs-lookup"><span data-stu-id="1a7fc-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1a7fc-109">[in]   O número máximo solicitado de tokens para colocar em `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="1a7fc-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="1a7fc-110">[out] Um ponteiro para o número de tokens são colocados em `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="1a7fc-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a7fc-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1a7fc-111">Return Value</span></span>  
  
|<span data-ttu-id="1a7fc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1a7fc-112">HRESULT</span></span>|<span data-ttu-id="1a7fc-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a7fc-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParameterConstraints` <span data-ttu-id="1a7fc-114">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="1a7fc-114">returned successfully.</span></span>|  
|`S_FALSE`|`phEnum` <span data-ttu-id="1a7fc-115">não tem nenhum elemento de membro.</span><span class="sxs-lookup"><span data-stu-id="1a7fc-115">has no member elements.</span></span> <span data-ttu-id="1a7fc-116">Nesse caso, `pcGenericParameterConstraints` é definido como 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="1a7fc-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a7fc-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1a7fc-117">Requirements</span></span>  
 <span data-ttu-id="1a7fc-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a7fc-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a7fc-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1a7fc-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1a7fc-120">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="1a7fc-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="1a7fc-121">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="1a7fc-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1a7fc-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a7fc-122">See also</span></span>

- [<span data-ttu-id="1a7fc-123">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="1a7fc-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="1a7fc-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="1a7fc-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
