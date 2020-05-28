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
ms.openlocfilehash: ac6de9a16fad6ba9d14f3960ddd28c42c111f254
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009386"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="3fb66-102">Método IMetaDataAssemblyImport::FindExportedTypeByName</span><span class="sxs-lookup"><span data-stu-id="3fb66-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="3fb66-103">Obtém um ponteiro para um tipo exportado, dado seu nome e tipo de delimitador.</span><span class="sxs-lookup"><span data-stu-id="3fb66-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fb66-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3fb66-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fb66-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3fb66-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="3fb66-106">no O nome do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="3fb66-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="3fb66-107">no O token de metadados para a classe de circunscrição do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="3fb66-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="3fb66-108">Esse valor é `mdExportedTypeNil` se o tipo exportado solicitado não for um tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="3fb66-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="3fb66-109">fora Um ponteiro para o `mdExportedType` token que representa o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="3fb66-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fb66-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="3fb66-110">Remarks</span></span>  
 <span data-ttu-id="3fb66-111">O `FindExportedTypeByName` método usa as regras padrão empregadas pelo Common Language Runtime para resolver referências.</span><span class="sxs-lookup"><span data-stu-id="3fb66-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fb66-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3fb66-112">Requirements</span></span>  
 <span data-ttu-id="3fb66-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fb66-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fb66-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3fb66-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3fb66-115">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3fb66-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3fb66-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fb66-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb66-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="3fb66-117">See also</span></span>

- [<span data-ttu-id="3fb66-118">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="3fb66-118">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="3fb66-119">Como o runtime localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="3fb66-119">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
