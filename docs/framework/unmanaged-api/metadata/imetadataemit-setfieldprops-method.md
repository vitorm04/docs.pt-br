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
ms.openlocfilehash: b921118f7c43edef3c07cbb34cbbd9119d36ce51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177550"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="b5a46-102">Método IMetaDataEmit::SetFieldProps</span><span class="sxs-lookup"><span data-stu-id="b5a46-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="b5a46-103">Define ou atualiza o valor padrão para o campo referenciado pelo token de campo especificado.</span><span class="sxs-lookup"><span data-stu-id="b5a46-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5a46-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5a46-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5a46-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="b5a46-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="b5a46-106">[em] O símbolo para o campo alvo.</span><span class="sxs-lookup"><span data-stu-id="b5a46-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="b5a46-107">[em] Atributos de campo.</span><span class="sxs-lookup"><span data-stu-id="b5a46-107">[in] Field attributes.</span></span> <span data-ttu-id="b5a46-108">Isto é uma `CorFieldAttr` pequena máscara de valores.</span><span class="sxs-lookup"><span data-stu-id="b5a46-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="b5a46-109">[em] O `ELEMENT_TYPE_` *\** pelo valor constante.</span><span class="sxs-lookup"><span data-stu-id="b5a46-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="b5a46-110">Isso é `CorElementType` um valor.</span><span class="sxs-lookup"><span data-stu-id="b5a46-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="b5a46-111">Se uma constante não estiver sendo `ELEMENT_TYPE_END`definida, defina esse valor para .</span><span class="sxs-lookup"><span data-stu-id="b5a46-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="b5a46-112">[em] O valor constante para o campo.</span><span class="sxs-lookup"><span data-stu-id="b5a46-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="b5a46-113">[em] O tamanho, em caracteres `pValue`Unicode, de .</span><span class="sxs-lookup"><span data-stu-id="b5a46-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5a46-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5a46-114">Requirements</span></span>  
 <span data-ttu-id="b5a46-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5a46-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5a46-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b5a46-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b5a46-117">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b5a46-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5a46-118">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5a46-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5a46-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="b5a46-119">See also</span></span>

- [<span data-ttu-id="b5a46-120">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b5a46-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b5a46-121">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b5a46-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
