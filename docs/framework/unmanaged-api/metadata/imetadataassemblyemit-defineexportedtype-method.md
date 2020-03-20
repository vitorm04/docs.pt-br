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
ms.openlocfilehash: 388f227377ddf73fe1297e1c777bb1c0607c13d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177878"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="81caa-102">Método IMetaDataAssemblyEmit::DefineExportedType</span><span class="sxs-lookup"><span data-stu-id="81caa-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="81caa-103">Cria `ExportedType` uma estrutura contendo metadados para o tipo exportado especificado e retorna o token de metadados associado.</span><span class="sxs-lookup"><span data-stu-id="81caa-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81caa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81caa-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81caa-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="81caa-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="81caa-106">[em] O nome do tipo a ser exportado.</span><span class="sxs-lookup"><span data-stu-id="81caa-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="81caa-107">Para a versão 1.1 do tempo de execução do idioma comum, `TypeDef` o nome do tipo exportado deve corresponder exatamente ao nome dado no para o tipo.</span><span class="sxs-lookup"><span data-stu-id="81caa-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="81caa-108">[em] Um token especificando onde o tipo exportado é implementado.</span><span class="sxs-lookup"><span data-stu-id="81caa-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="81caa-109">Os valores válidos e seus significados associados são:</span><span class="sxs-lookup"><span data-stu-id="81caa-109">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="81caa-110">`mdFile`O tipo é implementado em um arquivo diferente dentro deste conjunto.</span><span class="sxs-lookup"><span data-stu-id="81caa-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="81caa-111">`mdAssemblyRef`O tipo é implementado em uma montagem diferente.</span><span class="sxs-lookup"><span data-stu-id="81caa-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="81caa-112">`mdExportedTYpe`O tipo está aninhado dentro de algum outro tipo.</span><span class="sxs-lookup"><span data-stu-id="81caa-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="81caa-113">`mdFileNil`O tipo está no mesmo arquivo do manifesto e não é um tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="81caa-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="81caa-114">[em] Um token para os metadados que especifica o tipo a ser exportado.</span><span class="sxs-lookup"><span data-stu-id="81caa-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="81caa-115">Esse valor é `TypeDef` inserido na tabela do arquivo que implementa o tipo e só é relevante se esse arquivo estiver neste conjunto.</span><span class="sxs-lookup"><span data-stu-id="81caa-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="81caa-116">[em] Uma combinação bitwise dos valores de enumeração [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) que definem as configurações de propriedade para o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="81caa-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="81caa-117">[fora] Um ponteiro para o token de metadados retornado que indica o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="81caa-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81caa-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="81caa-118">Remarks</span></span>  
 <span data-ttu-id="81caa-119">Uma `ExportedType` estrutura de metadados deve ser definida para cada tipo que é exposto por esta montagem e que é implementada em um módulo diferente daquele que contém o manifesto.</span><span class="sxs-lookup"><span data-stu-id="81caa-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81caa-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81caa-120">Requirements</span></span>  
 <span data-ttu-id="81caa-121">**Plataforma:** Consulte [os requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81caa-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81caa-122">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="81caa-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="81caa-123">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="81caa-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="81caa-124">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81caa-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81caa-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="81caa-125">See also</span></span>

- [<span data-ttu-id="81caa-126">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="81caa-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
