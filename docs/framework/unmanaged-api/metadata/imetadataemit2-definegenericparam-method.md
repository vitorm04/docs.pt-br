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
ms.openlocfilehash: 027547098edefdca71317b8f885e71f468dc6e77
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777194"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="701fa-102">Método IMetaDataEmit2::DefineGenericParam</span><span class="sxs-lookup"><span data-stu-id="701fa-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="701fa-103">Cria uma definição para um parâmetro de tipo genérico e obtém um token para esse parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="701fa-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="701fa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="701fa-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="701fa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="701fa-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="701fa-106">[in] Uma `mdTypeDef` ou `mdMethodDef` token que representa o método ou construtor para o qual definir um parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="701fa-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="701fa-107">[in] O índice do parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="701fa-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="701fa-108">[in] Um valor igual a [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeração que descreve o tipo para o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="701fa-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="701fa-109">[in] O nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="701fa-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="701fa-110">[in] Esse parâmetro é reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="701fa-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="701fa-111">[in] Uma matriz terminada em zero de restrições de tipo.</span><span class="sxs-lookup"><span data-stu-id="701fa-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="701fa-112">Membros da matriz devem ser um `mdTypeDef`, `mdTypeRef`, ou `mdTypeSpec` token de metadados.</span><span class="sxs-lookup"><span data-stu-id="701fa-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="701fa-113">[out] Um token que representa o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="701fa-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="701fa-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="701fa-114">Requirements</span></span>  
 <span data-ttu-id="701fa-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="701fa-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="701fa-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="701fa-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="701fa-117">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="701fa-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="701fa-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="701fa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="701fa-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="701fa-119">See also</span></span>

- [<span data-ttu-id="701fa-120">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="701fa-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="701fa-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="701fa-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
