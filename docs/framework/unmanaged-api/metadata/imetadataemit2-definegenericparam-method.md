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
ms.openlocfilehash: 1868d13a9dbb73dbdf64e49c395bdbff02ce89d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177450"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="a302c-102">Método IMetaDataEmit2::DefineGenericParam</span><span class="sxs-lookup"><span data-stu-id="a302c-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="a302c-103">Cria uma definição para um parâmetro de tipo genérico, e obtém um token para esse parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="a302c-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a302c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a302c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a302c-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="a302c-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a302c-106">[em] Um `mdTypeDef` `mdMethodDef` ou token que representa o método ou construtor para o qual definir um parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="a302c-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="a302c-107">[em] O índice do parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="a302c-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="a302c-108">[em] Um valor da enumeração [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) que descreve o tipo para o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="a302c-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="a302c-109">[em] O nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a302c-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="a302c-110">[em] Este parâmetro é reservado para a extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="a302c-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="a302c-111">[em] Uma matriz de restrições de tipo com término zero.</span><span class="sxs-lookup"><span data-stu-id="a302c-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="a302c-112">Os membros da `mdTypeDef` `mdTypeRef`matriz `mdTypeSpec` devem ser um token de metadados ou de metadados.</span><span class="sxs-lookup"><span data-stu-id="a302c-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="a302c-113">[fora] Um símbolo que representa o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="a302c-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a302c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a302c-114">Requirements</span></span>  
 <span data-ttu-id="a302c-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a302c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a302c-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a302c-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a302c-117">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a302c-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a302c-118">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a302c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a302c-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="a302c-119">See also</span></span>

- [<span data-ttu-id="a302c-120">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="a302c-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="a302c-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="a302c-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
