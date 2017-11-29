---
title: "Método IMetaDataImport::FindTypeRef"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindTypeRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d742033788e270f01ee0cea70569ca65e7f35697
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="9dbed-102">Método IMetaDataImport::FindTypeRef</span><span class="sxs-lookup"><span data-stu-id="9dbed-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="9dbed-103">Obtém um ponteiro para o TypeRef token para o <xref:System.Type> referência que está no escopo especificado e que tem o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="9dbed-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dbed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9dbed-104">Syntax</span></span>  
  
```  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9dbed-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9dbed-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="9dbed-106">[in] Um token de ModuleRef, AssemblyRef ou TypeRef que especifica o módulo, assembly ou tipo, respectivamente, no qual o tipo de referência é definido.</span><span class="sxs-lookup"><span data-stu-id="9dbed-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="9dbed-107">[in] O nome da referência de tipo a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="9dbed-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="9dbed-108">[out] Um ponteiro para o token TypeRef correspondente.</span><span class="sxs-lookup"><span data-stu-id="9dbed-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dbed-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9dbed-109">Requirements</span></span>  
 <span data-ttu-id="9dbed-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dbed-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dbed-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9dbed-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9dbed-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9dbed-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9dbed-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dbed-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dbed-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9dbed-114">See Also</span></span>  
 [<span data-ttu-id="9dbed-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="9dbed-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9dbed-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="9dbed-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
