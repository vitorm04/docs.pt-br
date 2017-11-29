---
title: "Método IMetaDataEmit::DefineMemberRef"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineMemberRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4dc4cd317e0e540aaa774cbf9c4c7a2a2ffa40be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="5911b-102">Método IMetaDataEmit::DefineMemberRef</span><span class="sxs-lookup"><span data-stu-id="5911b-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="5911b-103">Define uma referência a um membro de um módulo fora do escopo atual e recebe um token para que a definição de referência.</span><span class="sxs-lookup"><span data-stu-id="5911b-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5911b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5911b-104">Syntax</span></span>  
  
```  
HRESULT DefineMemberRef (   
    [in]  mdToken           tkImport,   
    [in]  LPCWSTR           szName,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMemberRef       *pmr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5911b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5911b-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="5911b-106">[in] Token de classe ou a interface, o membro de destino se o membro não for global; Se o membro for global, o `mdModuleRef` token para outro arquivo.</span><span class="sxs-lookup"><span data-stu-id="5911b-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="5911b-107">[in] O nome do membro de destino.</span><span class="sxs-lookup"><span data-stu-id="5911b-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="5911b-108">[in] A assinatura do membro de destino.</span><span class="sxs-lookup"><span data-stu-id="5911b-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="5911b-109">[in] A contagem de bytes em `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="5911b-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="5911b-110">[out] O `mdMemberRef` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="5911b-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5911b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5911b-111">Requirements</span></span>  
 <span data-ttu-id="5911b-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5911b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5911b-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5911b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5911b-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="5911b-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5911b-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5911b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5911b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5911b-116">See Also</span></span>  
 [<span data-ttu-id="5911b-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="5911b-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="5911b-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="5911b-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
