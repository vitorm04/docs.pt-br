---
title: Método IMetaDataEmit::SetModuleProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce8be38f6e146b2a8669ea5c694353615f6f2d66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445897"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="c03ea-102">Método IMetaDataEmit::SetModuleProps</span><span class="sxs-lookup"><span data-stu-id="c03ea-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="c03ea-103">Atualiza as referências a um módulo definido por uma chamada anterior ao [Definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="c03ea-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c03ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c03ea-104">Syntax</span></span>  
  
```  
HRESULT SetModuleProps (   
    [in]  LPCWSTR     szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c03ea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c03ea-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="c03ea-106">[in] O nome do módulo em Unicode.</span><span class="sxs-lookup"><span data-stu-id="c03ea-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="c03ea-107">Este é o nome de arquivo e não o nome de caminho completo.</span><span class="sxs-lookup"><span data-stu-id="c03ea-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c03ea-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c03ea-108">Requirements</span></span>  
 <span data-ttu-id="c03ea-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c03ea-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c03ea-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c03ea-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c03ea-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c03ea-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c03ea-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c03ea-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c03ea-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c03ea-113">See Also</span></span>  
 [<span data-ttu-id="c03ea-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="c03ea-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="c03ea-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="c03ea-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
