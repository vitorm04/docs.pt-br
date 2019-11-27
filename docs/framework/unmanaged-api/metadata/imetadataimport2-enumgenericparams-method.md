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
ms.openlocfilehash: d0377ade5265bba9b313d6ed2e91c446497fac6e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428312"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="42f06-102">Método IMetaDataImport2::EnumGenericParams</span><span class="sxs-lookup"><span data-stu-id="42f06-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="42f06-103">Obtém um enumerador para uma matriz de tokens de parâmetro genéricos associados ao TypeDef ou token MethodDef especificado.</span><span class="sxs-lookup"><span data-stu-id="42f06-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42f06-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42f06-104">Syntax</span></span>  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,   
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],   
   [in]  ULONG            cMax,   
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42f06-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="42f06-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="42f06-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="42f06-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="42f06-107">no O TypeDef ou o token MethodDef cujos parâmetros genéricos devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="42f06-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="42f06-108">fora A matriz de parâmetros genéricos a ser enumerada.</span><span class="sxs-lookup"><span data-stu-id="42f06-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="42f06-109">no O número máximo solicitado de tokens a serem colocados no `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="42f06-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="42f06-110">fora O número retornado de tokens colocados em `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="42f06-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42f06-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="42f06-111">Return Value</span></span>  
  
|<span data-ttu-id="42f06-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="42f06-112">HRESULT</span></span>|<span data-ttu-id="42f06-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="42f06-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="42f06-114">`EnumGenericParams` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="42f06-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="42f06-115">`phEnum` não tem elementos de membro.</span><span class="sxs-lookup"><span data-stu-id="42f06-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="42f06-116">Nesse caso, `pcGenericParams` é definido como 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="42f06-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42f06-117">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="42f06-117">Requirements</span></span>  
 <span data-ttu-id="42f06-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42f06-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42f06-119">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="42f06-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="42f06-120">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="42f06-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="42f06-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42f06-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42f06-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42f06-122">See also</span></span>

- [<span data-ttu-id="42f06-123">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="42f06-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="42f06-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="42f06-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
