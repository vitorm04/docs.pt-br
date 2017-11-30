---
title: "Método ImportFile2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportFile2
api_location: alink.dll
api_type: COM
f1_keywords: ImportFile2
helpviewer_keywords: ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4d7e842152e84992124ec29cd551c3b5d50a6d61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="importfile2-method"></a><span data-ttu-id="70a40-102">Método ImportFile2</span><span class="sxs-lookup"><span data-stu-id="70a40-102">ImportFile2 Method</span></span>
<span data-ttu-id="70a40-103">Importa os assemblies e módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="70a40-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="70a40-104">Esse método é como [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), mas funciona mesmo se o arquivo que está sendo importado não existe no disco.</span><span class="sxs-lookup"><span data-stu-id="70a40-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70a40-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70a40-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="70a40-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="70a40-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="70a40-107">Nome do arquivo a ser importado.</span><span class="sxs-lookup"><span data-stu-id="70a40-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="70a40-108">Nome de arquivo de saída opcional que pode ser usado para renomear o arquivo como ele está vinculado no assembly.</span><span class="sxs-lookup"><span data-stu-id="70a40-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="70a40-109">Escopo opcional [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="70a40-109">Optional scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="70a40-110">Se TRUE, ImportTypes é usado, caso contrário, a importação deve ser executada manualmente.</span><span class="sxs-lookup"><span data-stu-id="70a40-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="70a40-111">Recebe a ID do arquivo ou assembly.</span><span class="sxs-lookup"><span data-stu-id="70a40-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="70a40-112">Recebe o [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="70a40-112">Receives the [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="70a40-113">NULL se o arquivo não é um assembly.</span><span class="sxs-lookup"><span data-stu-id="70a40-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="70a40-114">Recebe o encontrado de arquivos e/ou importados de escopos.</span><span class="sxs-lookup"><span data-stu-id="70a40-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70a40-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="70a40-115">Return Value</span></span>  
 <span data-ttu-id="70a40-116">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="70a40-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70a40-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="70a40-117">Requirements</span></span>  
 <span data-ttu-id="70a40-118">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="70a40-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70a40-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70a40-119">See Also</span></span>  
 [<span data-ttu-id="70a40-120">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="70a40-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="70a40-121">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="70a40-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="70a40-122">API do ALink</span><span class="sxs-lookup"><span data-stu-id="70a40-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
