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
ms.openlocfilehash: edfe5de9c9d7ef9607a2eea5146194bbd4393a92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175987"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="b8ef9-102">Método IMetaDataAssemblyImport::FindExportedTypeByName</span><span class="sxs-lookup"><span data-stu-id="b8ef9-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="b8ef9-103">Obtém um ponteiro para um tipo exportado, dado o seu nome e tipo de fechamento.</span><span class="sxs-lookup"><span data-stu-id="b8ef9-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8ef9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8ef9-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8ef9-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="b8ef9-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="b8ef9-106">[em] O nome do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="b8ef9-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="b8ef9-107">[em] O token de metadados para a classe de fechamento do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="b8ef9-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="b8ef9-108">Este valor `mdExportedTypeNil` é se o tipo exportado solicitado não for um tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="b8ef9-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="b8ef9-109">[fora] Um ponteiro `mdExportedType` para o token que representa o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="b8ef9-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8ef9-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8ef9-110">Remarks</span></span>  
 <span data-ttu-id="b8ef9-111">O `FindExportedTypeByName` método usa as regras padrão empregadas pelo tempo de execução da linguagem comum para resolver referências.</span><span class="sxs-lookup"><span data-stu-id="b8ef9-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8ef9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8ef9-112">Requirements</span></span>  
 <span data-ttu-id="b8ef9-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8ef9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8ef9-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b8ef9-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8ef9-115">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b8ef9-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b8ef9-116">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8ef9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8ef9-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="b8ef9-117">See also</span></span>

- [<span data-ttu-id="b8ef9-118">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="b8ef9-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="b8ef9-119">Como o runtime localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="b8ef9-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
