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
ms.openlocfilehash: 813460aa027b259866b168d426fd28502b5c4465
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432502"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="06df2-102">Método IMetaDataEmit::SetParamProps</span><span class="sxs-lookup"><span data-stu-id="06df2-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="06df2-103">Define ou altera recursos de um parâmetro de método que foi definido por uma chamada anterior para [IMetaDataEmit::D efineparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="06df2-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06df2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06df2-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="06df2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="06df2-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="06df2-106">no O token para o parâmetro de destino.</span><span class="sxs-lookup"><span data-stu-id="06df2-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="06df2-107">no O nome do parâmetro em Unicode.</span><span class="sxs-lookup"><span data-stu-id="06df2-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="06df2-108">no Os sinalizadores para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="06df2-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="06df2-109">no O ELEMENT_TYPE_ \* para o valor constante.</span><span class="sxs-lookup"><span data-stu-id="06df2-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="06df2-110">no O valor da constante para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="06df2-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="06df2-111">no O tamanho em caracteres (Unicode) de `pValue`.</span><span class="sxs-lookup"><span data-stu-id="06df2-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06df2-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="06df2-112">Requirements</span></span>  
 <span data-ttu-id="06df2-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06df2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06df2-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="06df2-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="06df2-115">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="06df2-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="06df2-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06df2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06df2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06df2-117">See also</span></span>

- [<span data-ttu-id="06df2-118">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="06df2-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="06df2-119">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="06df2-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
