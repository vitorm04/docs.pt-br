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
ms.openlocfilehash: 3898b095809e2b84f71aba2036f4d7a294dfdf6a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444659"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="1b9e5-102">Método IMetaDataEmit2::DefineGenericParam</span><span class="sxs-lookup"><span data-stu-id="1b9e5-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="1b9e5-103">Cria uma definição para um parâmetro de tipo genérico e Obtém um token para esse parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="1b9e5-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b9e5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b9e5-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1b9e5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1b9e5-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1b9e5-106">no Um `mdTypeDef` ou `mdMethodDef` token que representa o método ou construtor para o qual definir um parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="1b9e5-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="1b9e5-107">no O índice do parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="1b9e5-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="1b9e5-108">no Um valor da enumeração [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) que descreve o tipo para o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="1b9e5-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="1b9e5-109">no O nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1b9e5-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="1b9e5-110">no Esse parâmetro é reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="1b9e5-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="1b9e5-111">no Uma matriz de restrições de tipo terminada em zero.</span><span class="sxs-lookup"><span data-stu-id="1b9e5-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="1b9e5-112">Os membros da matriz devem ser um `mdTypeDef`, `mdTypeRef`ou `mdTypeSpec` token de metadados.</span><span class="sxs-lookup"><span data-stu-id="1b9e5-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="1b9e5-113">fora Um token que representa o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="1b9e5-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b9e5-114">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="1b9e5-114">Requirements</span></span>  
 <span data-ttu-id="1b9e5-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b9e5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b9e5-116">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1b9e5-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b9e5-117">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1b9e5-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b9e5-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b9e5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b9e5-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b9e5-119">See also</span></span>

- [<span data-ttu-id="1b9e5-120">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="1b9e5-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="1b9e5-121">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="1b9e5-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
