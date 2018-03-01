---
title: "Método IMetaDataImport::FindTypeRef"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3321f8ea1897f807a06d5c9a812fded2fd7f6365
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="f6176-102">Método IMetaDataImport::FindTypeRef</span><span class="sxs-lookup"><span data-stu-id="f6176-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="f6176-103">Obtém um ponteiro para o TypeRef token para o <xref:System.Type> referência que está no escopo especificado e que tem o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="f6176-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6176-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6176-104">Syntax</span></span>  
  
```  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6176-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f6176-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="f6176-106">[in] Um token de ModuleRef, AssemblyRef ou TypeRef que especifica o módulo, assembly ou tipo, respectivamente, no qual o tipo de referência é definido.</span><span class="sxs-lookup"><span data-stu-id="f6176-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="f6176-107">[in] O nome da referência de tipo a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="f6176-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="f6176-108">[out] Um ponteiro para o token TypeRef correspondente.</span><span class="sxs-lookup"><span data-stu-id="f6176-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6176-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6176-109">Requirements</span></span>  
 <span data-ttu-id="f6176-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6176-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6176-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f6176-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f6176-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f6176-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f6176-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6176-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6176-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6176-114">See Also</span></span>  
 [<span data-ttu-id="f6176-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="f6176-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="f6176-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="f6176-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
