---
title: Método IMetaDataAssemblyEmit::DefineManifestResource
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
ms.openlocfilehash: 83170815f4aa65988bb6a6394bd466a0ba376ebf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432057"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="da03a-102">Método IMetaDataAssemblyEmit::DefineManifestResource</span><span class="sxs-lookup"><span data-stu-id="da03a-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="da03a-103">Cria uma estrutura de `ManifestResource` que contém metadados para o recurso de manifesto especificado e retorna o token de metadados associado.</span><span class="sxs-lookup"><span data-stu-id="da03a-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da03a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da03a-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da03a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="da03a-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="da03a-106">no O nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="da03a-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="da03a-107">no Um token de metadados do tipo `mdtFile` ou `mdtAssemblyRef` que mapeia para o provedor de recursos.</span><span class="sxs-lookup"><span data-stu-id="da03a-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="da03a-108">Um valor nulo indica que o arquivo no qual os metadados são inseridos é o provedor de recursos.</span><span class="sxs-lookup"><span data-stu-id="da03a-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="da03a-109">no O deslocamento para o início do recurso dentro do arquivo.</span><span class="sxs-lookup"><span data-stu-id="da03a-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="da03a-110">Para recursos em arquivos autônomos, isso sempre será zero.</span><span class="sxs-lookup"><span data-stu-id="da03a-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="da03a-111">Se o recurso for inserido em um arquivo PE (executável portátil), esse será um deslocamento do BLOB de recursos, que começa no local especificado no arquivo de cabeçalho cor. h.</span><span class="sxs-lookup"><span data-stu-id="da03a-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="da03a-112">no Uma combinação de bits de valores de sinalizador que especifica configurações de propriedades para a definição de recurso.</span><span class="sxs-lookup"><span data-stu-id="da03a-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="da03a-113">fora Um ponteiro para o token de metadados retornado.</span><span class="sxs-lookup"><span data-stu-id="da03a-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da03a-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="da03a-114">Remarks</span></span>  
 <span data-ttu-id="da03a-115">Uma estrutura de metadados `ManifestResource` deve ser definida para cada recurso que é implementado em cada um dos arquivos do assembly.</span><span class="sxs-lookup"><span data-stu-id="da03a-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da03a-116">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="da03a-116">Requirements</span></span>  
 <span data-ttu-id="da03a-117">**Plataforma:** Consulte [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da03a-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da03a-118">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="da03a-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da03a-119">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="da03a-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="da03a-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da03a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da03a-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da03a-121">See also</span></span>

- [<span data-ttu-id="da03a-122">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="da03a-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
