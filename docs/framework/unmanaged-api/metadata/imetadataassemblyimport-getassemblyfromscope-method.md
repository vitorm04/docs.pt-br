---
title: Método IMetaDataAssemblyImport::GetAssemblyFromScope
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope method [.NET Framework metadata]
- GetAssemblyFromScope method [.NET Framework metadata]
ms.assetid: 0b437f70-561d-48c7-abe0-0cb9ace10c08
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d4797c952bfec4e0863e7a12b97e038c7ff8d95
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191517"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="3fd85-102">Método IMetaDataAssemblyImport::GetAssemblyFromScope</span><span class="sxs-lookup"><span data-stu-id="3fd85-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="3fd85-103">Obtém um ponteiro para o assembly no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="3fd85-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fd85-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3fd85-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fd85-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3fd85-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="3fd85-106">[out] Um ponteiro para recuperada `mdAssembly` token que identifica o assembly.</span><span class="sxs-lookup"><span data-stu-id="3fd85-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fd85-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3fd85-107">Requirements</span></span>  
 <span data-ttu-id="3fd85-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fd85-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fd85-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3fd85-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3fd85-110">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3fd85-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3fd85-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fd85-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd85-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3fd85-112">See also</span></span>

- [<span data-ttu-id="3fd85-113">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="3fd85-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
