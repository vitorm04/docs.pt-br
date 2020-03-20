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
ms.openlocfilehash: 2807458549db02598ba05f2aa80fa6ea6fbc5a13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177702"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="d9e79-102">Método IMetaDataEmit::DefineParam</span><span class="sxs-lookup"><span data-stu-id="d9e79-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="d9e79-103">Cria uma definição de parâmetro com a assinatura especificada para o método referenciado pelo token especificado e obtém um token para a definição desse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d9e79-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9e79-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9e79-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d9e79-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="d9e79-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="d9e79-106">[em] O token para o método cujo parâmetro está sendo definido.</span><span class="sxs-lookup"><span data-stu-id="d9e79-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="d9e79-107">[em] O número da seqüência de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d9e79-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="d9e79-108">[em] O nome do parâmetro em Unicode.</span><span class="sxs-lookup"><span data-stu-id="d9e79-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="d9e79-109">[em] Bandeiras para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d9e79-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="d9e79-110">Isto é uma `CorParamAttr` pequena máscara de valores.</span><span class="sxs-lookup"><span data-stu-id="d9e79-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="d9e79-111">[em] `ELEMENT_TYPE_` pelo valor *\** constante.</span><span class="sxs-lookup"><span data-stu-id="d9e79-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="d9e79-112">[em] O valor constante para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d9e79-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="d9e79-113">[em] O tamanho, em caracteres `pValue`Unicode, de .</span><span class="sxs-lookup"><span data-stu-id="d9e79-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="d9e79-114">[fora] O `mdParamDef` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="d9e79-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9e79-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9e79-115">Remarks</span></span>  
 <span data-ttu-id="d9e79-116">Os valores `ulParamSeq` de seqüência começam com 1 para parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d9e79-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="d9e79-117">Um valor de retorno tem um número de seqüência de 0.</span><span class="sxs-lookup"><span data-stu-id="d9e79-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9e79-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d9e79-118">Requirements</span></span>  
 <span data-ttu-id="d9e79-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9e79-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9e79-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d9e79-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9e79-121">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9e79-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9e79-122">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9e79-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e79-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="d9e79-123">See also</span></span>

- [<span data-ttu-id="d9e79-124">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="d9e79-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d9e79-125">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="d9e79-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
