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
ms.openlocfilehash: f52f102102cb654035d49eea0f4b0a9061475a3a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128811"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="d59fe-102">Método IMetaDataEmit::DefineModuleRef</span><span class="sxs-lookup"><span data-stu-id="d59fe-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="d59fe-103">Cria a assinatura de metadados para um módulo com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="d59fe-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d59fe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d59fe-104">Syntax</span></span>  
  
```  
HRESULT DefineModuleRef (     
    [in]  LPCWSTR           szName,   
    [out] mdModuleRef       *pmur   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d59fe-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d59fe-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="d59fe-106">[in] O nome do arquivo de metadados, normalmente uma DLL.</span><span class="sxs-lookup"><span data-stu-id="d59fe-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="d59fe-107">Isso é apenas o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="d59fe-107">This is the file name only.</span></span> <span data-ttu-id="d59fe-108">Não use um nome de caminho completo.</span><span class="sxs-lookup"><span data-stu-id="d59fe-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="d59fe-109">[out] Atribuído `mdModuleRef` token.</span><span class="sxs-lookup"><span data-stu-id="d59fe-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d59fe-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d59fe-110">Requirements</span></span>  
 <span data-ttu-id="d59fe-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d59fe-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d59fe-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d59fe-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d59fe-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d59fe-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d59fe-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d59fe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d59fe-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d59fe-115">See also</span></span>

- [<span data-ttu-id="d59fe-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="d59fe-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d59fe-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="d59fe-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
