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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b617e29e2df22b59114c8b978daa645de1cc6176
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186713"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="0c839-102">Método IMetaDataAssemblyEmit::DefineManifestResource</span><span class="sxs-lookup"><span data-stu-id="0c839-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="0c839-103">Cria um `ManifestResource` estrutura que contém metadados para o recurso de manifesto especificado e retorna o token de metadados associados.</span><span class="sxs-lookup"><span data-stu-id="0c839-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c839-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c839-104">Syntax</span></span>  
  
```  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c839-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0c839-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="0c839-106">[in] O nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="0c839-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="0c839-107">[in] Um token de metadados do tipo `mdtFile` ou `mdtAssemblyRef` que é mapeado para o provedor de recursos.</span><span class="sxs-lookup"><span data-stu-id="0c839-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="0c839-108">Um valor NULL indica que o arquivo no qual os metadados é inserido é o provedor de recursos.</span><span class="sxs-lookup"><span data-stu-id="0c839-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="0c839-109">[in] O deslocamento para o início do recurso dentro do arquivo.</span><span class="sxs-lookup"><span data-stu-id="0c839-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="0c839-110">Para obter recursos em arquivos autônomos, isso sempre será zero.</span><span class="sxs-lookup"><span data-stu-id="0c839-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="0c839-111">Se o recurso estiver incorporado em um arquivo de PE (executável portátil), esse é um deslocamento do recurso BLOB, que é iniciado no local especificado no arquivo de cabeçalho cor.h.</span><span class="sxs-lookup"><span data-stu-id="0c839-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="0c839-112">[in] Uma combinação bit a bit dos valores de sinalizador que especificam configurações de propriedade para a definição de recurso.</span><span class="sxs-lookup"><span data-stu-id="0c839-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="0c839-113">[out] Um ponteiro para o token de metadados retornados.</span><span class="sxs-lookup"><span data-stu-id="0c839-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c839-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="0c839-114">Remarks</span></span>  
 <span data-ttu-id="0c839-115">Um `ManifestResource` estrutura de metadados deve ser definida para cada recurso que é implementado em cada um dos arquivos do assembly.</span><span class="sxs-lookup"><span data-stu-id="0c839-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c839-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0c839-116">Requirements</span></span>  
 <span data-ttu-id="0c839-117">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c839-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c839-118">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0c839-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0c839-119">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0c839-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="0c839-120">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="0c839-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0c839-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c839-121">See also</span></span>

- [<span data-ttu-id="0c839-122">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="0c839-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
