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
ms.openlocfilehash: 220556ec130c7bff7c413405820c4fee0582b051
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008008"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="f0144-102">Método IMetaDataEmit::SetFieldProps</span><span class="sxs-lookup"><span data-stu-id="f0144-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="f0144-103">Define ou atualiza o valor padrão para o campo referenciado pelo token do campo especificado.</span><span class="sxs-lookup"><span data-stu-id="f0144-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0144-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f0144-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0144-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f0144-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="f0144-106">no O token para o campo de destino.</span><span class="sxs-lookup"><span data-stu-id="f0144-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="f0144-107">no Atributos de campo.</span><span class="sxs-lookup"><span data-stu-id="f0144-107">[in] Field attributes.</span></span> <span data-ttu-id="f0144-108">Esta é uma bitmask de `CorFieldAttr` valores.</span><span class="sxs-lookup"><span data-stu-id="f0144-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="f0144-109">no O `ELEMENT_TYPE_` *\** para o valor da constante.</span><span class="sxs-lookup"><span data-stu-id="f0144-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="f0144-110">Esse é um `CorElementType` valor.</span><span class="sxs-lookup"><span data-stu-id="f0144-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="f0144-111">Se uma constante não estiver sendo definida, defina esse valor como `ELEMENT_TYPE_END` .</span><span class="sxs-lookup"><span data-stu-id="f0144-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="f0144-112">no O valor constante para o campo.</span><span class="sxs-lookup"><span data-stu-id="f0144-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="f0144-113">no O tamanho, em caracteres Unicode, de `pValue` .</span><span class="sxs-lookup"><span data-stu-id="f0144-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0144-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f0144-114">Requirements</span></span>  
 <span data-ttu-id="f0144-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0144-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0144-116">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f0144-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f0144-117">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f0144-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0144-118">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0144-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0144-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="f0144-119">See also</span></span>

- [<span data-ttu-id="f0144-120">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f0144-120">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="f0144-121">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f0144-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
