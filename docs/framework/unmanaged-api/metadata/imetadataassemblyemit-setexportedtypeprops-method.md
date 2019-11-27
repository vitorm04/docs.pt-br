---
title: Método IMetaDataAssemblyEmit::SetExportedTypeProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
ms.openlocfilehash: ae682c354a7a5188611b103008a3e18f8d821260
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431934"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="65047-102">Método IMetaDataAssemblyEmit::SetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="65047-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="65047-103">Modifica a estrutura de metadados de `ExportedType` especificada.</span><span class="sxs-lookup"><span data-stu-id="65047-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65047-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65047-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65047-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="65047-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="65047-106">no O token de metadados que especifica a estrutura de metadados `ExportedType` a ser modificada.</span><span class="sxs-lookup"><span data-stu-id="65047-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="65047-107">no O token, do tipo `File`, `AssemblyRef`ou `ExportedType`, que especifica como esse tipo é implementado.</span><span class="sxs-lookup"><span data-stu-id="65047-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="65047-108">no O token de `TypeDef` referenciado no arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="65047-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="65047-109">no Uma combinação de bits de valores que especifica atributos do tipo.</span><span class="sxs-lookup"><span data-stu-id="65047-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65047-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="65047-110">Remarks</span></span>  
 <span data-ttu-id="65047-111">Para criar uma estrutura de metadados `ExportedType`, use o método [IMetaDataAssemblyEmit::D efineexportedtype](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="65047-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65047-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="65047-112">Requirements</span></span>  
 <span data-ttu-id="65047-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65047-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65047-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="65047-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65047-115">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="65047-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="65047-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65047-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65047-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65047-117">See also</span></span>

- [<span data-ttu-id="65047-118">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="65047-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
