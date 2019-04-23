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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f244d256d3af104d1d0c65769e82a87d6de046e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189001"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="d3ed9-102">Método IMetaDataEmit::DefineSecurityAttributeSet</span><span class="sxs-lookup"><span data-stu-id="d3ed9-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="d3ed9-103">Cria um conjunto de permissões de segurança para anexar ao objeto referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="d3ed9-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3ed9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3ed9-104">Syntax</span></span>  
  
```  
HRESULT DefineSecurityAttributeSet (   
    [in]  mdToken       tkObj,   
    [in]  COR_SECATTR   rSecAttrs[],   
    [in]  ULONG         cSecAttrs,   
    [out] ULONG         *pulErrorAttr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3ed9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d3ed9-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="d3ed9-106">[in] O token ao qual as informações de segurança estão anexadas.</span><span class="sxs-lookup"><span data-stu-id="d3ed9-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="d3ed9-107">[in] Uma matriz de `COR_SECATTR` estruturas.</span><span class="sxs-lookup"><span data-stu-id="d3ed9-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="d3ed9-108">[in] O número de elementos em `rSecAttrs`.</span><span class="sxs-lookup"><span data-stu-id="d3ed9-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="d3ed9-109">[out] Se o método falhar, especifica o índice no `rSecAttrs` do elemento que causou o problema.</span><span class="sxs-lookup"><span data-stu-id="d3ed9-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3ed9-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d3ed9-110">Requirements</span></span>  
 <span data-ttu-id="d3ed9-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3ed9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3ed9-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d3ed9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3ed9-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d3ed9-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3ed9-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3ed9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ed9-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3ed9-115">See also</span></span>

- [<span data-ttu-id="d3ed9-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="d3ed9-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d3ed9-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="d3ed9-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
