---
title: Método IMetaDataAssemblyImport::FindExportedTypeByName
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindExportedTypeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a70c041bc17f58a5e17877dd2e1f2aa2944e689
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777926"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="3df4d-102">Método IMetaDataAssemblyImport::FindExportedTypeByName</span><span class="sxs-lookup"><span data-stu-id="3df4d-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="3df4d-103">Obtém um ponteiro para um tipo exportado, dado seu nome e tipo de fechamento.</span><span class="sxs-lookup"><span data-stu-id="3df4d-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3df4d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3df4d-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3df4d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3df4d-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="3df4d-106">[in] O nome do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="3df4d-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="3df4d-107">[in] O token de metadados para a classe delimitadora do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="3df4d-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="3df4d-108">Esse valor é `mdExportedTypeNil` se exportado solicitada tipo não é um tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="3df4d-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="3df4d-109">[out] Um ponteiro para o `mdExportedType` token que representa o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="3df4d-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3df4d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="3df4d-110">Remarks</span></span>  
 <span data-ttu-id="3df4d-111">O `FindExportedTypeByName` método usa as regras padrão empregadas pelo common language runtime para resolver referências.</span><span class="sxs-lookup"><span data-stu-id="3df4d-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3df4d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3df4d-112">Requirements</span></span>  
 <span data-ttu-id="3df4d-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3df4d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3df4d-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3df4d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3df4d-115">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3df4d-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3df4d-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3df4d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3df4d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3df4d-117">See also</span></span>

- [<span data-ttu-id="3df4d-118">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="3df4d-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="3df4d-119">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="3df4d-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
