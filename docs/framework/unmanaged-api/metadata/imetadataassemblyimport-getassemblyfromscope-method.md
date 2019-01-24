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
ms.openlocfilehash: 7914257d167d0f54d3625d252076576e5e40296b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634929"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="db758-102">Método IMetaDataAssemblyImport::GetAssemblyFromScope</span><span class="sxs-lookup"><span data-stu-id="db758-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="db758-103">Obtém um ponteiro para o assembly no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="db758-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db758-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db758-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db758-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db758-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="db758-106">[out] Um ponteiro para recuperada `mdAssembly` token que identifica o assembly.</span><span class="sxs-lookup"><span data-stu-id="db758-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db758-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db758-107">Requirements</span></span>  
 <span data-ttu-id="db758-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db758-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db758-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="db758-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db758-110">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="db758-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db758-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db758-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db758-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db758-112">See also</span></span>
- [<span data-ttu-id="db758-113">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="db758-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
