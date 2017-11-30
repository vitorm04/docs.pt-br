---
title: "Método IMetaDataAssemblyImport::FindManifestResourceByName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindManifestResourceByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 492f8a50c421df56d1b2f79d15d86ef3251b401e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="90485-102">Método IMetaDataAssemblyImport::FindManifestResourceByName</span><span class="sxs-lookup"><span data-stu-id="90485-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="90485-103">Obtém um ponteiro para o recurso de manifesto com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="90485-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90485-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90485-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="90485-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="90485-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="90485-106">[in] O nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="90485-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="90485-107">[out] A matriz usada para armazenar o `mdManifestResource` tokens de metadados, cada um deles representa um recurso de manifesto.</span><span class="sxs-lookup"><span data-stu-id="90485-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90485-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="90485-108">Remarks</span></span>  
 <span data-ttu-id="90485-109">O `FindManifestResourceByName` método usa as regras padrão usadas pelo common language runtime para resolver referências.</span><span class="sxs-lookup"><span data-stu-id="90485-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90485-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90485-110">Requirements</span></span>  
 <span data-ttu-id="90485-111">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90485-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90485-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="90485-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="90485-113">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="90485-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="90485-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90485-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90485-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90485-115">See Also</span></span>  
 [<span data-ttu-id="90485-116">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="90485-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="90485-117">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="90485-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
