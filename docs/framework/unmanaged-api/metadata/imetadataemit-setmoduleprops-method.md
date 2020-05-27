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
ms.openlocfilehash: aee258c49e6726ebef990257456fd273b01b9ef0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007839"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="2ddb4-102">Método IMetaDataEmit::SetModuleProps</span><span class="sxs-lookup"><span data-stu-id="2ddb4-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="2ddb4-103">Atualiza referências a um módulo definido por uma chamada anterior para [IMetaDataEmit::D efinemoduleref](imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="2ddb4-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ddb4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ddb4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ddb4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2ddb4-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="2ddb4-106">no O nome do módulo em Unicode.</span><span class="sxs-lookup"><span data-stu-id="2ddb4-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="2ddb4-107">Esse é o nome do arquivo apenas e não o nome completo do caminho.</span><span class="sxs-lookup"><span data-stu-id="2ddb4-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ddb4-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ddb4-108">Requirements</span></span>  
 <span data-ttu-id="2ddb4-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ddb4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ddb4-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2ddb4-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2ddb4-111">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2ddb4-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ddb4-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ddb4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ddb4-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="2ddb4-113">See also</span></span>

- [<span data-ttu-id="2ddb4-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="2ddb4-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="2ddb4-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="2ddb4-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
