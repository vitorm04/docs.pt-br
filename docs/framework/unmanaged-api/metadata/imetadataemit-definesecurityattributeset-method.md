---
title: Método IMetaDataEmit::DefineSecurityAttributeSet
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineSecurityAttributeSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet
helpviewer_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet method [.NET Framework metadata]
- DefineSecurityAttributeSet method [.NET Framework metadata]
ms.assetid: 27064ca2-4186-4433-90a7-3b297785e891
topic_type:
- apiref
ms.openlocfilehash: b98fab6c6127c3f78151d3b84160d4ca0434b6cd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428251"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="a3334-102">Método IMetaDataEmit::DefineSecurityAttributeSet</span><span class="sxs-lookup"><span data-stu-id="a3334-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="a3334-103">Cria um conjunto de permissões de segurança para anexar ao objeto referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="a3334-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3334-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3334-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineSecurityAttributeSet (   
    [in]  mdToken       tkObj,   
    [in]  COR_SECATTR   rSecAttrs[],   
    [in]  ULONG         cSecAttrs,   
    [out] ULONG         *pulErrorAttr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3334-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a3334-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="a3334-106">no O token ao qual as informações de segurança estão anexadas.</span><span class="sxs-lookup"><span data-stu-id="a3334-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="a3334-107">no Uma matriz de estruturas de `COR_SECATTR`.</span><span class="sxs-lookup"><span data-stu-id="a3334-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="a3334-108">no O número de elementos no `rSecAttrs`.</span><span class="sxs-lookup"><span data-stu-id="a3334-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="a3334-109">fora Se o método falhar, especifica o índice em `rSecAttrs` do elemento que causou o problema.</span><span class="sxs-lookup"><span data-stu-id="a3334-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3334-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a3334-110">Requirements</span></span>  
 <span data-ttu-id="a3334-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3334-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3334-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a3334-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a3334-113">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a3334-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3334-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3334-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3334-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3334-115">See also</span></span>

- [<span data-ttu-id="a3334-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="a3334-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a3334-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="a3334-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
