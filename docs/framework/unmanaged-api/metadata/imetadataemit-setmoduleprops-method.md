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
ms.openlocfilehash: 2d3c820975488fa722e7af6070611ba7e9686ce8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445452"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="3021e-102">Método IMetaDataEmit::SetModuleProps</span><span class="sxs-lookup"><span data-stu-id="3021e-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="3021e-103">Atualiza referências a um módulo definido por uma chamada anterior para [IMetaDataEmit::D efinemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="3021e-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3021e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3021e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (   
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3021e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3021e-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="3021e-106">no O nome do módulo em Unicode.</span><span class="sxs-lookup"><span data-stu-id="3021e-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="3021e-107">Esse é o nome do arquivo apenas e não o nome completo do caminho.</span><span class="sxs-lookup"><span data-stu-id="3021e-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3021e-108">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="3021e-108">Requirements</span></span>  
 <span data-ttu-id="3021e-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3021e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3021e-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3021e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3021e-111">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3021e-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3021e-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3021e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3021e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3021e-113">See also</span></span>

- [<span data-ttu-id="3021e-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="3021e-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3021e-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="3021e-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
