---
title: Método IMetaDataEmit::DefineParam
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 86711d107636505ab7aa23f0f72f70bd3e27635d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992648"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="bab2a-102">Método IMetaDataEmit::DefineParam</span><span class="sxs-lookup"><span data-stu-id="bab2a-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="bab2a-103">Cria uma definição de parâmetro com a assinatura especificada para o método referenciado pelo token especificado e obtém um token para essa definição de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bab2a-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bab2a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bab2a-104">Syntax</span></span>  
  
```  
HRESULT DefineParam (  
    [in]  mdMethodDef md,   
    [in]  ULONG       ulParamSeq,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,   
    [out] mdParamDef  *ppd   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bab2a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bab2a-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="bab2a-106">[in] O token para o método cujo parâmetro está sendo definido.</span><span class="sxs-lookup"><span data-stu-id="bab2a-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="bab2a-107">[in] O número de sequência do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bab2a-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="bab2a-108">[in] O nome do parâmetro no Unicode.</span><span class="sxs-lookup"><span data-stu-id="bab2a-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="bab2a-109">[in] Sinalizadores para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bab2a-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="bab2a-110">Esse é um bitmask de `CorParamAttr` valores.</span><span class="sxs-lookup"><span data-stu-id="bab2a-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="bab2a-111">[in] `ELEMENT_TYPE_` *\** para o valor da constante.</span><span class="sxs-lookup"><span data-stu-id="bab2a-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="bab2a-112">[in] O valor da constante para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bab2a-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="bab2a-113">[in] O tamanho, em caracteres Unicode, de `pValue`.</span><span class="sxs-lookup"><span data-stu-id="bab2a-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="bab2a-114">[out] O `mdParamDef` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="bab2a-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bab2a-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="bab2a-115">Remarks</span></span>  
 <span data-ttu-id="bab2a-116">Os valores de sequência no `ulParamSeq` começam com 1 para parâmetros.</span><span class="sxs-lookup"><span data-stu-id="bab2a-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="bab2a-117">Um valor de retorno tem um número de sequência igual a 0.</span><span class="sxs-lookup"><span data-stu-id="bab2a-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bab2a-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bab2a-118">Requirements</span></span>  
 <span data-ttu-id="bab2a-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bab2a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bab2a-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bab2a-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bab2a-121">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="bab2a-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bab2a-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bab2a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bab2a-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bab2a-123">See also</span></span>

- [<span data-ttu-id="bab2a-124">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="bab2a-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bab2a-125">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="bab2a-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
