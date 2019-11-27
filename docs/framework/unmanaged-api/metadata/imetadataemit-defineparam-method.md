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
ms.openlocfilehash: 5c81bc82e19bce658336e4860a61f2721e17423d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431693"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="e55f6-102">Método IMetaDataEmit::DefineParam</span><span class="sxs-lookup"><span data-stu-id="e55f6-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="e55f6-103">Cria uma definição de parâmetro com a assinatura especificada para o método referenciado pelo token especificado e Obtém um token para essa definição de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e55f6-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e55f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e55f6-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="e55f6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e55f6-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="e55f6-106">no O token para o método cujo parâmetro está sendo definido.</span><span class="sxs-lookup"><span data-stu-id="e55f6-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="e55f6-107">no O número de sequência do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e55f6-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="e55f6-108">no O nome do parâmetro em Unicode.</span><span class="sxs-lookup"><span data-stu-id="e55f6-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="e55f6-109">no Sinalizadores para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e55f6-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="e55f6-110">Este é um bitmask de valores de `CorParamAttr`.</span><span class="sxs-lookup"><span data-stu-id="e55f6-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="e55f6-111">[in] `ELEMENT_TYPE_` *\** para o valor constante.</span><span class="sxs-lookup"><span data-stu-id="e55f6-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="e55f6-112">no O valor da constante para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e55f6-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="e55f6-113">no O tamanho, em caracteres Unicode, de `pValue`.</span><span class="sxs-lookup"><span data-stu-id="e55f6-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="e55f6-114">fora O token de `mdParamDef` atribuído.</span><span class="sxs-lookup"><span data-stu-id="e55f6-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e55f6-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="e55f6-115">Remarks</span></span>  
 <span data-ttu-id="e55f6-116">Os valores de sequência em `ulParamSeq` começam com 1 para parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e55f6-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="e55f6-117">Um valor de retorno tem um número de sequência de 0.</span><span class="sxs-lookup"><span data-stu-id="e55f6-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e55f6-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e55f6-118">Requirements</span></span>  
 <span data-ttu-id="e55f6-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e55f6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e55f6-120">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e55f6-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e55f6-121">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e55f6-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e55f6-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e55f6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e55f6-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e55f6-123">See also</span></span>

- [<span data-ttu-id="e55f6-124">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="e55f6-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e55f6-125">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="e55f6-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
