---
title: Método IMetaDataAssemblyEmit::DefineExportedType
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 81d6c972b53221ee53cbcf31639d65c30858b48b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008151"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="210ed-102">Método IMetaDataAssemblyEmit::DefineExportedType</span><span class="sxs-lookup"><span data-stu-id="210ed-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="210ed-103">Cria uma `ExportedType` estrutura que contém metadados para o tipo exportado especificado e retorna o token de metadados associado.</span><span class="sxs-lookup"><span data-stu-id="210ed-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="210ed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="210ed-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="210ed-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="210ed-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="210ed-106">no O nome do tipo a ser exportado.</span><span class="sxs-lookup"><span data-stu-id="210ed-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="210ed-107">Para a versão 1,1 do Common Language Runtime, o nome do tipo exportado deve corresponder exatamente ao nome fornecido no `TypeDef` para o tipo.</span><span class="sxs-lookup"><span data-stu-id="210ed-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="210ed-108">no Um token que especifica onde o tipo exportado é implementado.</span><span class="sxs-lookup"><span data-stu-id="210ed-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="210ed-109">Os valores válidos e seus significados associados são:</span><span class="sxs-lookup"><span data-stu-id="210ed-109">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="210ed-110">`mdFile`O tipo é implementado em um arquivo diferente dentro desse assembly.</span><span class="sxs-lookup"><span data-stu-id="210ed-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="210ed-111">`mdAssemblyRef`O tipo é implementado em um assembly diferente.</span><span class="sxs-lookup"><span data-stu-id="210ed-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="210ed-112">`mdExportedTYpe`O tipo é aninhado em algum outro tipo.</span><span class="sxs-lookup"><span data-stu-id="210ed-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="210ed-113">`mdFileNil`O tipo está no mesmo arquivo que o manifesto e não é um tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="210ed-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="210ed-114">no Um token para os metadados que especifica o tipo a ser exportado.</span><span class="sxs-lookup"><span data-stu-id="210ed-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="210ed-115">Esse valor é inserido na `TypeDef` tabela no arquivo que implementa o tipo e é relevante apenas se esse arquivo estiver nesse assembly.</span><span class="sxs-lookup"><span data-stu-id="210ed-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="210ed-116">no Uma combinação de bits de [CorTypeAttr](cortypeattr-enumeration.md) de valores de enumeração que define as configurações de propriedade para o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="210ed-116">[in] A bitwise combination of [CorTypeAttr](cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="210ed-117">fora Um ponteiro para o token de metadados retornado que indica o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="210ed-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="210ed-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="210ed-118">Remarks</span></span>  
 <span data-ttu-id="210ed-119">Uma `ExportedType` estrutura de metadados deve ser definida para cada tipo que é exposto por esse assembly e implementada em um módulo diferente daquele que contém o manifesto.</span><span class="sxs-lookup"><span data-stu-id="210ed-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="210ed-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="210ed-120">Requirements</span></span>  
 <span data-ttu-id="210ed-121">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="210ed-121">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="210ed-122">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="210ed-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="210ed-123">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="210ed-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="210ed-124">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="210ed-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="210ed-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="210ed-125">See also</span></span>

- [<span data-ttu-id="210ed-126">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="210ed-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
