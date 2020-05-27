---
title: Método IMetaDataEmit::SetParamProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
ms.openlocfilehash: b710f966f519e2702607b7e186fff5986110d391
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007813"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="d67bd-102">Método IMetaDataEmit::SetParamProps</span><span class="sxs-lookup"><span data-stu-id="d67bd-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="d67bd-103">Define ou altera recursos de um parâmetro de método que foi definido por uma chamada anterior para [IMetaDataEmit::D efineparam](imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="d67bd-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d67bd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d67bd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParamProps (
    [in]  mdParamDef  pd,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d67bd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d67bd-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="d67bd-106">no O token para o parâmetro de destino.</span><span class="sxs-lookup"><span data-stu-id="d67bd-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="d67bd-107">no O nome do parâmetro em Unicode.</span><span class="sxs-lookup"><span data-stu-id="d67bd-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="d67bd-108">no Os sinalizadores para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d67bd-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="d67bd-109">no O ELEMENT_TYPE_ \* para o valor constante.</span><span class="sxs-lookup"><span data-stu-id="d67bd-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="d67bd-110">no O valor da constante para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d67bd-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="d67bd-111">no O tamanho em caracteres (Unicode) de `pValue` .</span><span class="sxs-lookup"><span data-stu-id="d67bd-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d67bd-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d67bd-112">Requirements</span></span>  
 <span data-ttu-id="d67bd-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d67bd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d67bd-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d67bd-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d67bd-115">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d67bd-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d67bd-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d67bd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d67bd-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="d67bd-117">See also</span></span>

- [<span data-ttu-id="d67bd-118">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="d67bd-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d67bd-119">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="d67bd-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
