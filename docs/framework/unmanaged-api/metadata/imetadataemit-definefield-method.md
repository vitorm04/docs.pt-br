---
title: Método IMetaDataEmit::DefineField
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b54ceb099df15855b6b30b8c28d7d8917a9c71eb
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184943"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="919bc-102">Método IMetaDataEmit::DefineField</span><span class="sxs-lookup"><span data-stu-id="919bc-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="919bc-103">Cria uma definição para um campo com a assinatura de metadados especificado e obtém um token para essa definição de campo.</span><span class="sxs-lookup"><span data-stu-id="919bc-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="919bc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="919bc-104">Syntax</span></span>  
  
```  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="919bc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="919bc-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="919bc-106">[in] O `mdTypeDef` token para a classe ou interface delimitador.</span><span class="sxs-lookup"><span data-stu-id="919bc-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="919bc-107">[in] O nome do campo em Unicode.</span><span class="sxs-lookup"><span data-stu-id="919bc-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="919bc-108">[in] Os atributos de campo.</span><span class="sxs-lookup"><span data-stu-id="919bc-108">[in] The field attributes.</span></span> <span data-ttu-id="919bc-109">Esse é um bitmask de `CorFieldAttr` valores.</span><span class="sxs-lookup"><span data-stu-id="919bc-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="919bc-110">[in] A assinatura de campo como um BLOB.</span><span class="sxs-lookup"><span data-stu-id="919bc-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="919bc-111">[in] A contagem de bytes em `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="919bc-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="919bc-112">[in] O `ELEMENT_TYPE_` *\** para o valor da constante.</span><span class="sxs-lookup"><span data-stu-id="919bc-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="919bc-113">Esse é um `CorElementType` valor.</span><span class="sxs-lookup"><span data-stu-id="919bc-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="919bc-114">Se não definir um valor constante para o campo, use `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="919bc-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="919bc-115">[in] O valor da constante para o campo.</span><span class="sxs-lookup"><span data-stu-id="919bc-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="919bc-116">[in] O tamanho em caracteres (Unicode) do `pValue`.</span><span class="sxs-lookup"><span data-stu-id="919bc-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="919bc-117">[out] O `mdFieldDef` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="919bc-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="919bc-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="919bc-118">Requirements</span></span>  
 <span data-ttu-id="919bc-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="919bc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="919bc-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="919bc-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="919bc-121">**Biblioteca:** usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="919bc-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="919bc-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="919bc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="919bc-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="919bc-123">See Also</span></span>  
 [<span data-ttu-id="919bc-124">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="919bc-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="919bc-125">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="919bc-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
