---
title: "Método IMetaDataEmit::DefineSecurityAttributeSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineSecurityAttributeSet
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineSecurityAttributeSet
helpviewer_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet method [.NET Framework metadata]
- DefineSecurityAttributeSet method [.NET Framework metadata]
ms.assetid: 27064ca2-4186-4433-90a7-3b297785e891
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 79d5bb7240305d06d916e969765606ddc2ddf9b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="f6e2e-102">Método IMetaDataEmit::DefineSecurityAttributeSet</span><span class="sxs-lookup"><span data-stu-id="f6e2e-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="f6e2e-103">Cria um conjunto de permissões de segurança para anexar ao objeto referenciado por token especificado.</span><span class="sxs-lookup"><span data-stu-id="f6e2e-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6e2e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6e2e-104">Syntax</span></span>  
  
```  
HRESULT DefineSecurityAttributeSet (   
    [in]  mdToken       tkObj,   
    [in]  COR_SECATTR   rSecAttrs[],   
    [in]  ULONG         cSecAttrs,   
    [out] ULONG         *pulErrorAttr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6e2e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f6e2e-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="f6e2e-106">[in] O token ao qual as informações de segurança estão anexadas.</span><span class="sxs-lookup"><span data-stu-id="f6e2e-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="f6e2e-107">[in] Uma matriz de `COR_SECATTR` estruturas.</span><span class="sxs-lookup"><span data-stu-id="f6e2e-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="f6e2e-108">[in] O número de elementos em `rSecAttrs`.</span><span class="sxs-lookup"><span data-stu-id="f6e2e-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="f6e2e-109">[out] Se o método falhar, especifica o índice em `rSecAttrs` do elemento que causou o problema.</span><span class="sxs-lookup"><span data-stu-id="f6e2e-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6e2e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6e2e-110">Requirements</span></span>  
 <span data-ttu-id="f6e2e-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6e2e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6e2e-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f6e2e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f6e2e-113">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f6e2e-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6e2e-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6e2e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6e2e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6e2e-115">See Also</span></span>  
 [<span data-ttu-id="f6e2e-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f6e2e-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f6e2e-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f6e2e-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
