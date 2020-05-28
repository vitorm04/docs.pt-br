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
ms.openlocfilehash: ef6f7a1a6e86b45acce91792385bc3761dfb4c39
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009074"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="4c929-102">Método IMetaDataAssemblyImport::FindManifestResourceByName</span><span class="sxs-lookup"><span data-stu-id="4c929-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="4c929-103">Obtém um ponteiro para o recurso de manifesto com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="4c929-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c929-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c929-104">Syntax</span></span>  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,
    [out] mdManifestResource     *ptkManifestResource  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="4c929-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4c929-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="4c929-106">no O nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="4c929-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="4c929-107">fora A matriz usada para armazenar os `mdManifestResource` tokens de metadados, cada um representando um recurso de manifesto.</span><span class="sxs-lookup"><span data-stu-id="4c929-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c929-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="4c929-108">Remarks</span></span>  
 <span data-ttu-id="4c929-109">O `FindManifestResourceByName` método usa as regras padrão empregadas pelo Common Language Runtime para resolver referências.</span><span class="sxs-lookup"><span data-stu-id="4c929-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c929-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4c929-110">Requirements</span></span>  
 <span data-ttu-id="4c929-111">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c929-111">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c929-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4c929-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4c929-113">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4c929-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4c929-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c929-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c929-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="4c929-115">See also</span></span>

- [<span data-ttu-id="4c929-116">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="4c929-116">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="4c929-117">Como o runtime localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="4c929-117">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
