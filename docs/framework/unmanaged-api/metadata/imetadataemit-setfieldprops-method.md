---
title: Método IMetaDataEmit::SetFieldProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 94ba607669b4b1ca68294470cf1cc4fb27464d28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097649"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="e254d-102">Método IMetaDataEmit::SetFieldProps</span><span class="sxs-lookup"><span data-stu-id="e254d-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="e254d-103">Define ou atualiza o valor padrão para o campo referenciado pelo token de campo especificado.</span><span class="sxs-lookup"><span data-stu-id="e254d-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e254d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e254d-104">Syntax</span></span>  
  
```  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,   
    [in]  DWORD       dwFieldFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e254d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e254d-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="e254d-106">[in] O token para o campo de destino.</span><span class="sxs-lookup"><span data-stu-id="e254d-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="e254d-107">[in] Atributos de campo.</span><span class="sxs-lookup"><span data-stu-id="e254d-107">[in] Field attributes.</span></span> <span data-ttu-id="e254d-108">Esse é um bitmask de `CorFieldAttr` valores.</span><span class="sxs-lookup"><span data-stu-id="e254d-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="e254d-109">[in] O `ELEMENT_TYPE_` *\** para o valor da constante.</span><span class="sxs-lookup"><span data-stu-id="e254d-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="e254d-110">Esse é um `CorElementType` valor.</span><span class="sxs-lookup"><span data-stu-id="e254d-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="e254d-111">Se não estiver sendo definida uma constante, defina esse valor como `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="e254d-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="e254d-112">[in] O valor da constante para o campo.</span><span class="sxs-lookup"><span data-stu-id="e254d-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="e254d-113">[in] O tamanho, em caracteres Unicode, de `pValue`.</span><span class="sxs-lookup"><span data-stu-id="e254d-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e254d-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e254d-114">Requirements</span></span>  
 <span data-ttu-id="e254d-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e254d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e254d-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e254d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e254d-117">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e254d-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e254d-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e254d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e254d-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e254d-119">See also</span></span>

- [<span data-ttu-id="e254d-120">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="e254d-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e254d-121">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="e254d-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
