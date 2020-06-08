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
ms.openlocfilehash: af226f9317b67b23e03d06614ed5b9c956939c22
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503413"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="1d793-102">Método IMetaDataImport2::EnumGenericParamConstraints</span><span class="sxs-lookup"><span data-stu-id="1d793-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="1d793-103">Obtém um enumerador para uma matriz de restrições de parâmetro genérico associadas ao parâmetro genérico representado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="1d793-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d793-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d793-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d793-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1d793-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1d793-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="1d793-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="1d793-107">no   Um token que representa o parâmetro genérico cujas restrições devem ser enumeradas.</span><span class="sxs-lookup"><span data-stu-id="1d793-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="1d793-108">fora A matriz de restrições de parâmetro genérico para enumerar.</span><span class="sxs-lookup"><span data-stu-id="1d793-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1d793-109">no   O número máximo solicitado de tokens a serem colocados `rGenericParamConstraints` .</span><span class="sxs-lookup"><span data-stu-id="1d793-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="1d793-110">fora Um ponteiro para o número de tokens colocados em `rGenericParamConstraints` .</span><span class="sxs-lookup"><span data-stu-id="1d793-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d793-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="1d793-111">Return Value</span></span>  
  
|<span data-ttu-id="1d793-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1d793-112">HRESULT</span></span>|<span data-ttu-id="1d793-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d793-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1d793-114">`EnumGenericParameterConstraints`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="1d793-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1d793-115">`phEnum`Não tem elementos de membro.</span><span class="sxs-lookup"><span data-stu-id="1d793-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="1d793-116">Nesse caso, `pcGenericParameterConstraints` é definido como 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="1d793-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1d793-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1d793-117">Requirements</span></span>  
 <span data-ttu-id="1d793-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d793-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d793-119">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1d793-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1d793-120">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1d793-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1d793-121">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d793-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d793-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="1d793-122">See also</span></span>

- [<span data-ttu-id="1d793-123">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="1d793-123">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="1d793-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="1d793-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
