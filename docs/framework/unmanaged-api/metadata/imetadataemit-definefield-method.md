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
ms.openlocfilehash: 8ca5ab70f60de4d783800fb18612a8f04cb9cee1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177708"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="e6abb-102">Método IMetaDataEmit::DefineField</span><span class="sxs-lookup"><span data-stu-id="e6abb-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="e6abb-103">Cria uma definição para um campo com a assinatura de metadados especificada e obtém um token para essa definição de campo.</span><span class="sxs-lookup"><span data-stu-id="e6abb-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6abb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6abb-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="e6abb-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="e6abb-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="e6abb-106">[em] O `mdTypeDef` token para a classe de fechamento ou interface.</span><span class="sxs-lookup"><span data-stu-id="e6abb-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="e6abb-107">[em] O nome de campo em Unicode.</span><span class="sxs-lookup"><span data-stu-id="e6abb-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="e6abb-108">[em] Os atributos de campo.</span><span class="sxs-lookup"><span data-stu-id="e6abb-108">[in] The field attributes.</span></span> <span data-ttu-id="e6abb-109">Isto é uma `CorFieldAttr` pequena máscara de valores.</span><span class="sxs-lookup"><span data-stu-id="e6abb-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="e6abb-110">[em] A assinatura de campo como um BLOB.</span><span class="sxs-lookup"><span data-stu-id="e6abb-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="e6abb-111">[em] A contagem de `pvSigBlob`bytes em .</span><span class="sxs-lookup"><span data-stu-id="e6abb-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="e6abb-112">[em] O `ELEMENT_TYPE_` *\** pelo valor constante.</span><span class="sxs-lookup"><span data-stu-id="e6abb-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="e6abb-113">Isso é `CorElementType` um valor.</span><span class="sxs-lookup"><span data-stu-id="e6abb-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="e6abb-114">Se não definir um valor constante `ELEMENT_TYPE_END`para o campo, use .</span><span class="sxs-lookup"><span data-stu-id="e6abb-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="e6abb-115">[em] O valor constante para o campo.</span><span class="sxs-lookup"><span data-stu-id="e6abb-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="e6abb-116">[em] O tamanho nos caracteres `pValue`(Unicode) de .</span><span class="sxs-lookup"><span data-stu-id="e6abb-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="e6abb-117">[fora] O `mdFieldDef` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="e6abb-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6abb-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6abb-118">Requirements</span></span>  
 <span data-ttu-id="e6abb-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6abb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6abb-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e6abb-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e6abb-121">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e6abb-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6abb-122">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6abb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6abb-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="e6abb-123">See also</span></span>

- [<span data-ttu-id="e6abb-124">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="e6abb-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e6abb-125">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="e6abb-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
