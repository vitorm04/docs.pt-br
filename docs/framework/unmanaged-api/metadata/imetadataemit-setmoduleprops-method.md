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
ms.openlocfilehash: 86cb99023c0abfc70d292427b14986dbcea1d333
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586157"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="9e661-102">Método IMetaDataEmit::SetModuleProps</span><span class="sxs-lookup"><span data-stu-id="9e661-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="9e661-103">Atualiza as referências a um módulo definido por uma chamada anterior ao [imetadataemit:: Definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="9e661-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e661-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e661-104">Syntax</span></span>  
  
```  
HRESULT SetModuleProps (   
    [in]  LPCWSTR     szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e661-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9e661-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="9e661-106">[in] O nome do módulo em Unicode.</span><span class="sxs-lookup"><span data-stu-id="9e661-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="9e661-107">Isso é apenas o nome do arquivo e não o nome de caminho completo.</span><span class="sxs-lookup"><span data-stu-id="9e661-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e661-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e661-108">Requirements</span></span>  
 <span data-ttu-id="9e661-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e661-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e661-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9e661-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9e661-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9e661-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e661-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e661-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e661-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e661-113">See also</span></span>
- [<span data-ttu-id="9e661-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="9e661-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9e661-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="9e661-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
