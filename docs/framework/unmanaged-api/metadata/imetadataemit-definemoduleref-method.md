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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19f1839aa2c4ca810e76c1745103a00c6f5ea5a3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777570"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="0efb0-102">Método IMetaDataEmit::DefineModuleRef</span><span class="sxs-lookup"><span data-stu-id="0efb0-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="0efb0-103">Cria a assinatura de metadados para um módulo com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="0efb0-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0efb0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0efb0-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineModuleRef (     
    [in]  LPCWSTR           szName,   
    [out] mdModuleRef       *pmur   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0efb0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0efb0-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="0efb0-106">[in] O nome do arquivo de metadados, normalmente uma DLL.</span><span class="sxs-lookup"><span data-stu-id="0efb0-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="0efb0-107">Isso é apenas o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="0efb0-107">This is the file name only.</span></span> <span data-ttu-id="0efb0-108">Não use um nome de caminho completo.</span><span class="sxs-lookup"><span data-stu-id="0efb0-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="0efb0-109">[out] Atribuído `mdModuleRef` token.</span><span class="sxs-lookup"><span data-stu-id="0efb0-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0efb0-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0efb0-110">Requirements</span></span>  
 <span data-ttu-id="0efb0-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0efb0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0efb0-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0efb0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0efb0-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0efb0-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0efb0-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0efb0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0efb0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0efb0-115">See also</span></span>

- [<span data-ttu-id="0efb0-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="0efb0-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0efb0-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="0efb0-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
