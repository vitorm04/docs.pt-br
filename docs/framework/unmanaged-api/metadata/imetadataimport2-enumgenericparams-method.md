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
ms.openlocfilehash: 093e3edf0a3c06222ebc56a4876fca08d1b7578f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490721"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="f4258-102">Método IMetaDataImport2::EnumGenericParams</span><span class="sxs-lookup"><span data-stu-id="f4258-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="f4258-103">Obtém um enumerador para uma matriz de tokens de parâmetro genéricos associados ao TypeDef ou token MethodDef especificado.</span><span class="sxs-lookup"><span data-stu-id="f4258-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4258-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f4258-104">Syntax</span></span>  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4258-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4258-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f4258-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="f4258-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="f4258-107">no O TypeDef ou o token MethodDef cujos parâmetros genéricos devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="f4258-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="f4258-108">fora A matriz de parâmetros genéricos a ser enumerada.</span><span class="sxs-lookup"><span data-stu-id="f4258-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f4258-109">no O número máximo solicitado de tokens a serem colocados `rGenericParams` .</span><span class="sxs-lookup"><span data-stu-id="f4258-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="f4258-110">fora O número retornado de tokens colocados em `rGenericParams` .</span><span class="sxs-lookup"><span data-stu-id="f4258-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4258-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="f4258-111">Return Value</span></span>  
  
|<span data-ttu-id="f4258-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f4258-112">HRESULT</span></span>|<span data-ttu-id="f4258-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4258-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f4258-114">`EnumGenericParams`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f4258-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f4258-115">`phEnum`Não tem elementos de membro.</span><span class="sxs-lookup"><span data-stu-id="f4258-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="f4258-116">Nesse caso, `pcGenericParams` é definido como 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="f4258-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f4258-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4258-117">Requirements</span></span>  
 <span data-ttu-id="f4258-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4258-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4258-119">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f4258-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f4258-120">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f4258-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f4258-121">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4258-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4258-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="f4258-122">See also</span></span>

- [<span data-ttu-id="f4258-123">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="f4258-123">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="f4258-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="f4258-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
