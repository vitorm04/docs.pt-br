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
ms.openlocfilehash: b3c145bae61922894f4893d532923319ccf16f85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499006"
---
# <a name="importfile2-method"></a><span data-ttu-id="1d2a1-102">Método ImportFile2</span><span class="sxs-lookup"><span data-stu-id="1d2a1-102">ImportFile2 Method</span></span>
<span data-ttu-id="1d2a1-103">Importa os assemblies e módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="1d2a1-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="1d2a1-104">Esse método é como [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), mas funciona mesmo se o arquivo que está sendo importado não existe no disco.</span><span class="sxs-lookup"><span data-stu-id="1d2a1-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d2a1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d2a1-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="1d2a1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1d2a1-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="1d2a1-107">Nome do arquivo a ser importado.</span><span class="sxs-lookup"><span data-stu-id="1d2a1-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="1d2a1-108">Nome de arquivo de saída opcional que pode ser usado para renomear o arquivo conforme ele é vinculado no assembly.</span><span class="sxs-lookup"><span data-stu-id="1d2a1-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="1d2a1-109">Escopo opcional [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="1d2a1-109">Optional scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="1d2a1-110">Se for TRUE, ImportTypes é usado, caso contrário, a importação deve ser executada manualmente.</span><span class="sxs-lookup"><span data-stu-id="1d2a1-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="1d2a1-111">Recebe a ID do arquivo ou assembly.</span><span class="sxs-lookup"><span data-stu-id="1d2a1-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="1d2a1-112">Recebe o [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="1d2a1-112">Receives the [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="1d2a1-113">NULL se o arquivo não é um assembly.</span><span class="sxs-lookup"><span data-stu-id="1d2a1-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="1d2a1-114">Recebe o encontrado de arquivos e/ou importados de escopos.</span><span class="sxs-lookup"><span data-stu-id="1d2a1-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d2a1-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1d2a1-115">Return Value</span></span>  
 <span data-ttu-id="1d2a1-116">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="1d2a1-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d2a1-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1d2a1-117">Requirements</span></span>  
 <span data-ttu-id="1d2a1-118">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="1d2a1-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d2a1-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d2a1-119">See also</span></span>
- [<span data-ttu-id="1d2a1-120">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="1d2a1-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="1d2a1-121">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="1d2a1-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="1d2a1-122">API do ALink</span><span class="sxs-lookup"><span data-stu-id="1d2a1-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
