---
title: "Método IMetaDataAssemblyImport::FindExportedTypeByName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 010e6c29541e4b55353db4359c018935c5e1ef2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="db850-102">Método IMetaDataAssemblyImport::FindExportedTypeByName</span><span class="sxs-lookup"><span data-stu-id="db850-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="db850-103">Obtém um ponteiro para um tipo exportado, dado seu nome e o tipo de delimitador.</span><span class="sxs-lookup"><span data-stu-id="db850-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db850-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db850-104">Syntax</span></span>  
  
```  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db850-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db850-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="db850-106">[in] O nome do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="db850-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="db850-107">[in] O token de metadados para a classe delimitador do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="db850-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="db850-108">Esse valor é `mdExportedTypeNil` se a solicitação exportado tipo não é um tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="db850-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="db850-109">[out] Um ponteiro para o `mdExportedType` token que representa o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="db850-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db850-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="db850-110">Remarks</span></span>  
 <span data-ttu-id="db850-111">O `FindExportedTypeByName` método usa as regras padrão usadas pelo common language runtime para resolver referências.</span><span class="sxs-lookup"><span data-stu-id="db850-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db850-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db850-112">Requirements</span></span>  
 <span data-ttu-id="db850-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db850-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db850-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="db850-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db850-115">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="db850-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db850-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db850-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db850-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db850-117">See Also</span></span>  
 [<span data-ttu-id="db850-118">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="db850-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="db850-119">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="db850-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
