---
title: "Método IMetaDataEmit::DefineModuleRef"
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
- IMetaDataEmit.DefineModuleRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2b745e216ca49ed5d226d6d531281880b43e4939
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="fa3f5-102">Método IMetaDataEmit::DefineModuleRef</span><span class="sxs-lookup"><span data-stu-id="fa3f5-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="fa3f5-103">Cria a assinatura de metadados para um módulo com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="fa3f5-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa3f5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa3f5-104">Syntax</span></span>  
  
```  
HRESULT DefineModuleRef (     
    [in]  LPCWSTR           szName,   
    [out] mdModuleRef       *pmur   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa3f5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fa3f5-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="fa3f5-106">[in] O nome do arquivo de metadados, normalmente uma DLL.</span><span class="sxs-lookup"><span data-stu-id="fa3f5-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="fa3f5-107">Este é o nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="fa3f5-107">This is the file name only.</span></span> <span data-ttu-id="fa3f5-108">Não use um nome de caminho completo.</span><span class="sxs-lookup"><span data-stu-id="fa3f5-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="fa3f5-109">[out] Atribuída `mdModuleRef` token.</span><span class="sxs-lookup"><span data-stu-id="fa3f5-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa3f5-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fa3f5-110">Requirements</span></span>  
 <span data-ttu-id="fa3f5-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa3f5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa3f5-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fa3f5-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fa3f5-113">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="fa3f5-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa3f5-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa3f5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa3f5-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa3f5-115">See Also</span></span>  
 [<span data-ttu-id="fa3f5-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="fa3f5-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="fa3f5-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="fa3f5-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
