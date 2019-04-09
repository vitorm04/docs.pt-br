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
ms.openlocfilehash: 7edd2eeafcce6a22c3256d0684a9c4f961b34002
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157632"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="cf093-102">Método IMetaDataImport2::EnumGenericParams</span><span class="sxs-lookup"><span data-stu-id="cf093-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="cf093-103">Obtém um enumerador para uma matriz genérica de tokens de parâmetro associados TypeDef especificado ou MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="cf093-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf093-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf093-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,   
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],   
   [in]  ULONG            cMax,   
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf093-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cf093-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="cf093-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="cf093-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="cf093-107">[in] O token de TypeDef ou MethodDef cujos parâmetros genéricos são a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="cf093-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="cf093-108">[out] A matriz de parâmetros genéricos para enumerar.</span><span class="sxs-lookup"><span data-stu-id="cf093-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cf093-109">[in] O número máximo solicitado de tokens para colocar em `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="cf093-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="cf093-110">[out] O número retornado de tokens são colocados em `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="cf093-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf093-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="cf093-111">Return Value</span></span>  
  
|<span data-ttu-id="cf093-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cf093-112">HRESULT</span></span>|<span data-ttu-id="cf093-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf093-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParams` <span data-ttu-id="cf093-114">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="cf093-114">returned successfully.</span></span>|  
|`S_FALSE`|`phEnum` <span data-ttu-id="cf093-115">não tem nenhum elemento de membro.</span><span class="sxs-lookup"><span data-stu-id="cf093-115">has no member elements.</span></span> <span data-ttu-id="cf093-116">Nesse caso, `pcGenericParams` é definido como 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="cf093-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf093-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cf093-117">Requirements</span></span>  
 <span data-ttu-id="cf093-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf093-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf093-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cf093-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf093-120">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="cf093-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="cf093-121">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="cf093-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cf093-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf093-122">See also</span></span>

- [<span data-ttu-id="cf093-123">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="cf093-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="cf093-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="cf093-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
