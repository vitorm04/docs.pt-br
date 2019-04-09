---
title: Método ImportFile2
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c6279c790e9b28e5f3bac93d5d0fdd411dd8c0d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127264"
---
# <a name="importfile2-method"></a><span data-ttu-id="43ad9-102">Método ImportFile2</span><span class="sxs-lookup"><span data-stu-id="43ad9-102">ImportFile2 Method</span></span>
<span data-ttu-id="43ad9-103">Importa os assemblies e módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="43ad9-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="43ad9-104">Esse método é como [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), mas funciona mesmo se o arquivo que está sendo importado não existe no disco.</span><span class="sxs-lookup"><span data-stu-id="43ad9-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ad9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43ad9-105">Syntax</span></span>  
  
```  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="43ad9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="43ad9-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="43ad9-107">Nome do arquivo a ser importado.</span><span class="sxs-lookup"><span data-stu-id="43ad9-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="43ad9-108">Nome de arquivo de saída opcional que pode ser usado para renomear o arquivo conforme ele é vinculado no assembly.</span><span class="sxs-lookup"><span data-stu-id="43ad9-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="43ad9-109">Escopo opcional [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="43ad9-109">Optional scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="43ad9-110">Se for TRUE, ImportTypes é usado, caso contrário, a importação deve ser executada manualmente.</span><span class="sxs-lookup"><span data-stu-id="43ad9-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="43ad9-111">Recebe a ID do arquivo ou assembly.</span><span class="sxs-lookup"><span data-stu-id="43ad9-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="43ad9-112">Recebe o [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="43ad9-112">Receives the [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="43ad9-113">NULL se o arquivo não é um assembly.</span><span class="sxs-lookup"><span data-stu-id="43ad9-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="43ad9-114">Recebe o encontrado de arquivos e/ou importados de escopos.</span><span class="sxs-lookup"><span data-stu-id="43ad9-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43ad9-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="43ad9-115">Return Value</span></span>  
 <span data-ttu-id="43ad9-116">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="43ad9-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43ad9-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="43ad9-117">Requirements</span></span>  
 <span data-ttu-id="43ad9-118">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="43ad9-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ad9-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43ad9-119">See also</span></span>

- [<span data-ttu-id="43ad9-120">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="43ad9-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="43ad9-121">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="43ad9-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="43ad9-122">API do ALink</span><span class="sxs-lookup"><span data-stu-id="43ad9-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
