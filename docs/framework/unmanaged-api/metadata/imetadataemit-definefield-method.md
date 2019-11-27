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
ms.openlocfilehash: 40f24a4ea628ce92a27ab1bfe97fc87a57dfa4f0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432551"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="5ffdf-102">Método IMetaDataEmit::DefineField</span><span class="sxs-lookup"><span data-stu-id="5ffdf-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="5ffdf-103">Cria uma definição para um campo com a assinatura de metadados especificada e Obtém um token para essa definição de campo.</span><span class="sxs-lookup"><span data-stu-id="5ffdf-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ffdf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ffdf-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="5ffdf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ffdf-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="5ffdf-106">no O token de `mdTypeDef` para a classe ou a interface de circunscrição.</span><span class="sxs-lookup"><span data-stu-id="5ffdf-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="5ffdf-107">no O nome do campo em Unicode.</span><span class="sxs-lookup"><span data-stu-id="5ffdf-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="5ffdf-108">no Os atributos do campo.</span><span class="sxs-lookup"><span data-stu-id="5ffdf-108">[in] The field attributes.</span></span> <span data-ttu-id="5ffdf-109">Este é um bitmask de valores de `CorFieldAttr`.</span><span class="sxs-lookup"><span data-stu-id="5ffdf-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="5ffdf-110">no A assinatura de campo como um BLOB.</span><span class="sxs-lookup"><span data-stu-id="5ffdf-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="5ffdf-111">no A contagem de bytes em `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="5ffdf-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="5ffdf-112">no O `ELEMENT_TYPE_` *\** para o valor constante.</span><span class="sxs-lookup"><span data-stu-id="5ffdf-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="5ffdf-113">Esse é um valor `CorElementType`.</span><span class="sxs-lookup"><span data-stu-id="5ffdf-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="5ffdf-114">Se não estiver definindo um valor constante para o campo, use `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="5ffdf-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="5ffdf-115">no O valor constante para o campo.</span><span class="sxs-lookup"><span data-stu-id="5ffdf-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="5ffdf-116">no O tamanho em caracteres (Unicode) de `pValue`.</span><span class="sxs-lookup"><span data-stu-id="5ffdf-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="5ffdf-117">fora O token de `mdFieldDef` atribuído.</span><span class="sxs-lookup"><span data-stu-id="5ffdf-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ffdf-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ffdf-118">Requirements</span></span>  
 <span data-ttu-id="5ffdf-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ffdf-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ffdf-120">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5ffdf-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5ffdf-121">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5ffdf-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ffdf-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ffdf-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ffdf-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ffdf-123">See also</span></span>

- [<span data-ttu-id="5ffdf-124">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="5ffdf-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5ffdf-125">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="5ffdf-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
