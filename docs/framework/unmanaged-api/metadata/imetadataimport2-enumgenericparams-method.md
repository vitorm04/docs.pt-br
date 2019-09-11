---
title: Método IMetaDataImport2::EnumGenericParams
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 39e3e71185051435afcf03d51ec62742c080b02a
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855704"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="9e048-102">Método IMetaDataImport2::EnumGenericParams</span><span class="sxs-lookup"><span data-stu-id="9e048-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="9e048-103">Obtém um enumerador para uma matriz de tokens de parâmetro genéricos associados ao TypeDef ou token MethodDef especificado.</span><span class="sxs-lookup"><span data-stu-id="9e048-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e048-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e048-104">Syntax</span></span>  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,   
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],   
   [in]  ULONG            cMax,   
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e048-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9e048-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9e048-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="9e048-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="9e048-107">no O TypeDef ou o token MethodDef cujos parâmetros genéricos devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="9e048-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="9e048-108">fora A matriz de parâmetros genéricos a ser enumerada.</span><span class="sxs-lookup"><span data-stu-id="9e048-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9e048-109">no O número máximo solicitado de tokens a serem `rGenericParams`colocados.</span><span class="sxs-lookup"><span data-stu-id="9e048-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="9e048-110">fora O número retornado de tokens colocados `rGenericParams`em.</span><span class="sxs-lookup"><span data-stu-id="9e048-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e048-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9e048-111">Return Value</span></span>  
  
|<span data-ttu-id="9e048-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e048-112">HRESULT</span></span>|<span data-ttu-id="9e048-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e048-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9e048-114">`EnumGenericParams`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9e048-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9e048-115">`phEnum`Não tem elementos de membro.</span><span class="sxs-lookup"><span data-stu-id="9e048-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="9e048-116">Nesse caso, `pcGenericParams` é definido como 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="9e048-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9e048-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e048-117">Requirements</span></span>  
 <span data-ttu-id="9e048-118">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e048-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e048-119">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9e048-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9e048-120">**Biblioteca** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9e048-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9e048-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e048-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e048-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e048-122">See also</span></span>

- [<span data-ttu-id="9e048-123">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="9e048-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="9e048-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="9e048-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
