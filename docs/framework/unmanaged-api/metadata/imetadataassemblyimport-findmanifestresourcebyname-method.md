---
title: Método IMetaDataAssemblyImport::FindManifestResourceByName
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindManifestResourceByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aaaae5bda88d1fbc9949a080c5765127fd112bde
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855958"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="b7ce7-102">Método IMetaDataAssemblyImport::FindManifestResourceByName</span><span class="sxs-lookup"><span data-stu-id="b7ce7-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="b7ce7-103">Obtém um ponteiro para o recurso de manifesto com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="b7ce7-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7ce7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7ce7-104">Syntax</span></span>  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="b7ce7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b7ce7-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="b7ce7-106">no O nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="b7ce7-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="b7ce7-107">fora A matriz usada para armazenar os `mdManifestResource` tokens de metadados, cada um representando um recurso de manifesto.</span><span class="sxs-lookup"><span data-stu-id="b7ce7-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7ce7-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7ce7-108">Remarks</span></span>  
 <span data-ttu-id="b7ce7-109">O `FindManifestResourceByName` método usa as regras padrão empregadas pelo Common Language Runtime para resolver referências.</span><span class="sxs-lookup"><span data-stu-id="b7ce7-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7ce7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7ce7-110">Requirements</span></span>  
 <span data-ttu-id="b7ce7-111">**Plataforma** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7ce7-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7ce7-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b7ce7-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7ce7-113">**Biblioteca** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b7ce7-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b7ce7-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7ce7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7ce7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7ce7-115">See also</span></span>

- [<span data-ttu-id="b7ce7-116">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="b7ce7-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="b7ce7-117">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="b7ce7-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
