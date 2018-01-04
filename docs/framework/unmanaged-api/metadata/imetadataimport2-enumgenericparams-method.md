---
title: "Método IMetaDataImport2::EnumGenericParams"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.EnumGenericParams
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da7a77bd1a758e4bb7fad3fcd15621176abc92a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="f514f-102">Método IMetaDataImport2::EnumGenericParams</span><span class="sxs-lookup"><span data-stu-id="f514f-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="f514f-103">Obtém um enumerador para uma matriz de parâmetro genérico tokens associado com o TypeDef especificado ou MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="f514f-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f514f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f514f-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,   
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],   
   [in]  ULONG            cMax,   
   [out] ULONG            *pcGenericParams  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f514f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f514f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f514f-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="f514f-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="f514f-107">[in] O token de TypeDef ou MethodDef cujos parâmetros genéricos devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="f514f-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="f514f-108">[out] A matriz de parâmetros genéricos para enumerar.</span><span class="sxs-lookup"><span data-stu-id="f514f-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f514f-109">[in] O número máximo solicitado de tokens para colocar em `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="f514f-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="f514f-110">[out] O número retornado de tokens são colocados em `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="f514f-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f514f-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f514f-111">Return Value</span></span>  
  
|<span data-ttu-id="f514f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f514f-112">HRESULT</span></span>|<span data-ttu-id="f514f-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f514f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f514f-114">`EnumGenericParams`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="f514f-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f514f-115">`phEnum`não tem nenhum elemento de membro.</span><span class="sxs-lookup"><span data-stu-id="f514f-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="f514f-116">Nesse caso, `pcGenericParams` é definido como 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="f514f-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f514f-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f514f-117">Requirements</span></span>  
 <span data-ttu-id="f514f-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f514f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f514f-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f514f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f514f-120">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f514f-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f514f-121">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f514f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f514f-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f514f-122">See Also</span></span>  
 [<span data-ttu-id="f514f-123">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="f514f-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="f514f-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="f514f-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
