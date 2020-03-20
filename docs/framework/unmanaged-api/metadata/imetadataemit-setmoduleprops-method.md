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
ms.openlocfilehash: 69c3ee366dbb8505e0df744037c480da996bb836
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175610"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="38080-102">Método IMetaDataEmit::SetModuleProps</span><span class="sxs-lookup"><span data-stu-id="38080-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="38080-103">Atualiza as referências a um módulo definido por uma chamada anterior ao [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="38080-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38080-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38080-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38080-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="38080-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="38080-106">[em] O nome do módulo em Unicode.</span><span class="sxs-lookup"><span data-stu-id="38080-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="38080-107">Este é apenas o nome do arquivo e não o nome completo do caminho.</span><span class="sxs-lookup"><span data-stu-id="38080-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38080-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38080-108">Requirements</span></span>  
 <span data-ttu-id="38080-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38080-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38080-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="38080-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38080-111">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="38080-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38080-112">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38080-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38080-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="38080-113">See also</span></span>

- [<span data-ttu-id="38080-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="38080-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="38080-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="38080-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
