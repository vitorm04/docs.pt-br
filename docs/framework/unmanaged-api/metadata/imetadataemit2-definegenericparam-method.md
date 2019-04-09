---
title: Método IMetaDataEmit2::DefineGenericParam
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de8547ed0ee83bafe4612bdcd62607fc94fb3f69
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163716"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="d2b50-102">Método IMetaDataEmit2::DefineGenericParam</span><span class="sxs-lookup"><span data-stu-id="d2b50-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="d2b50-103">Cria uma definição para um parâmetro de tipo genérico e obtém um token para esse parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="d2b50-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2b50-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2b50-104">Syntax</span></span>  
  
```  
HRESULT DefineGenericParam (   
    [in]  mdToken         tk,   
    [in]  ULONG           ulParamSeq,   
    [in]  DWORD           dwParamFlags,   
    [in]  LPCWSTR         szname,   
    [in]  DWORD           reserved,   
    [in]  mdToken         rtkConstraints[],   
    [out] mdGenericParam  *pgp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2b50-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d2b50-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="d2b50-106">[in] Uma `mdTypeDef` ou `mdMethodDef` token que representa o método ou construtor para o qual definir um parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="d2b50-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="d2b50-107">[in] O índice do parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="d2b50-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="d2b50-108">[in] Um valor igual a [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeração que descreve o tipo para o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="d2b50-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="d2b50-109">[in] O nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d2b50-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="d2b50-110">[in] Esse parâmetro é reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="d2b50-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="d2b50-111">[in] Uma matriz terminada em zero de restrições de tipo.</span><span class="sxs-lookup"><span data-stu-id="d2b50-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="d2b50-112">Membros da matriz devem ser um `mdTypeDef`, `mdTypeRef`, ou `mdTypeSpec` token de metadados.</span><span class="sxs-lookup"><span data-stu-id="d2b50-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="d2b50-113">[out] Um token que representa o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="d2b50-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2b50-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2b50-114">Requirements</span></span>  
 <span data-ttu-id="d2b50-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2b50-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2b50-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d2b50-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d2b50-117">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d2b50-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="d2b50-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="d2b50-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d2b50-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2b50-119">See also</span></span>

- [<span data-ttu-id="d2b50-120">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="d2b50-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="d2b50-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="d2b50-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
