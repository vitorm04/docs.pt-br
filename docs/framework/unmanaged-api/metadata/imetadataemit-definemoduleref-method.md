---
title: Método IMetaDataEmit::DefineModuleRef
ms.date: 03/30/2017
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
ms.openlocfilehash: 94261b7796166cf482a7de990551890e4722dd3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177730"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="90526-102">Método IMetaDataEmit::DefineModuleRef</span><span class="sxs-lookup"><span data-stu-id="90526-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="90526-103">Cria a assinatura de metadados para um módulo com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="90526-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90526-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90526-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineModuleRef (
    [in]  LPCWSTR           szName,
    [out] mdModuleRef       *pmur
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90526-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="90526-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="90526-106">[em] O nome do outro arquivo de metadados, tipicamente um DLL.</span><span class="sxs-lookup"><span data-stu-id="90526-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="90526-107">Este é apenas o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="90526-107">This is the file name only.</span></span> <span data-ttu-id="90526-108">Não use um nome de caminho completo.</span><span class="sxs-lookup"><span data-stu-id="90526-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="90526-109">[fora] O token atribuído. `mdModuleRef`</span><span class="sxs-lookup"><span data-stu-id="90526-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90526-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90526-110">Requirements</span></span>  
 <span data-ttu-id="90526-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90526-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90526-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="90526-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="90526-113">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90526-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90526-114">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90526-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90526-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="90526-115">See also</span></span>

- [<span data-ttu-id="90526-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="90526-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="90526-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="90526-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
