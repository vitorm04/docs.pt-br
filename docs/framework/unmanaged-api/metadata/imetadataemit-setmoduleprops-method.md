---
title: "Método IMetaDataEmit::SetModuleProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetModuleProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0653f0407486e09ab51ef05e74218207268b6e8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="c5fb3-102">Método IMetaDataEmit::SetModuleProps</span><span class="sxs-lookup"><span data-stu-id="c5fb3-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="c5fb3-103">Atualiza as referências a um módulo definido por uma chamada anterior ao [Definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="c5fb3-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5fb3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5fb3-104">Syntax</span></span>  
  
```  
HRESULT SetModuleProps (   
    [in]  LPCWSTR     szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5fb3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c5fb3-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="c5fb3-106">[in] O nome do módulo em Unicode.</span><span class="sxs-lookup"><span data-stu-id="c5fb3-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="c5fb3-107">Este é o nome de arquivo e não o nome de caminho completo.</span><span class="sxs-lookup"><span data-stu-id="c5fb3-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5fb3-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c5fb3-108">Requirements</span></span>  
 <span data-ttu-id="c5fb3-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5fb3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5fb3-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c5fb3-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5fb3-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c5fb3-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5fb3-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5fb3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5fb3-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5fb3-113">See Also</span></span>  
 [<span data-ttu-id="c5fb3-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="c5fb3-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="c5fb3-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="c5fb3-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
