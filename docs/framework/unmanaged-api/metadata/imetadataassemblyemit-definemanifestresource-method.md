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
ms.openlocfilehash: 5aa5d78faa8ca9261594e2a649b11088e1d78ee7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177864"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="02aa0-102">Método IMetaDataAssemblyEmit::DefineManifestResource</span><span class="sxs-lookup"><span data-stu-id="02aa0-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="02aa0-103">Cria `ManifestResource` uma estrutura contendo metadados para o recurso manifesto especificado e retorna o token de metadados associado.</span><span class="sxs-lookup"><span data-stu-id="02aa0-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02aa0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02aa0-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,
    [in] mdToken                tkImplementation,
    [in] DWORD                  dwOffset,
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02aa0-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="02aa0-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="02aa0-106">[em] O nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="02aa0-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="02aa0-107">[em] Um token de `mdtFile` metadados do tipo ou `mdtAssemblyRef` que mapeia para o provedor de recursos.</span><span class="sxs-lookup"><span data-stu-id="02aa0-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="02aa0-108">Um valor NULL indica que o arquivo no qual os metadados estão incorporados é o provedor de recursos.</span><span class="sxs-lookup"><span data-stu-id="02aa0-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="02aa0-109">[em] A compensação para o início do recurso dentro do arquivo.</span><span class="sxs-lookup"><span data-stu-id="02aa0-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="02aa0-110">Para recursos em arquivos autônomos, isso sempre será zero.</span><span class="sxs-lookup"><span data-stu-id="02aa0-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="02aa0-111">Se o recurso estiver incorporado em um arquivo PE (executável portátil), esta será uma compensação do recurso BLOB, que começa no local especificado no arquivo de cabeçalho cor.h.</span><span class="sxs-lookup"><span data-stu-id="02aa0-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="02aa0-112">[em] Uma combinação bitwise de valores de bandeira que especificam configurações de propriedade para a definição de recurso.</span><span class="sxs-lookup"><span data-stu-id="02aa0-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="02aa0-113">[fora] Um ponteiro para o token de metadados retornado.</span><span class="sxs-lookup"><span data-stu-id="02aa0-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02aa0-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="02aa0-114">Remarks</span></span>  
 <span data-ttu-id="02aa0-115">Uma `ManifestResource` estrutura de metadados deve ser definida para cada recurso que é implementado em cada um dos arquivos da montagem.</span><span class="sxs-lookup"><span data-stu-id="02aa0-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02aa0-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="02aa0-116">Requirements</span></span>  
 <span data-ttu-id="02aa0-117">**Plataforma:** Consulte [os requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02aa0-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02aa0-118">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="02aa0-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02aa0-119">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="02aa0-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="02aa0-120">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02aa0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02aa0-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="02aa0-121">See also</span></span>

- [<span data-ttu-id="02aa0-122">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="02aa0-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
