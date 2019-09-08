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
ms.openlocfilehash: a03fc24e5ef932d13c0d195f53c703cdd3ff45ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776930"
---
# <a name="importfile2-method"></a><span data-ttu-id="5d558-102">Método ImportFile2</span><span class="sxs-lookup"><span data-stu-id="5d558-102">ImportFile2 Method</span></span>
<span data-ttu-id="5d558-103">Importa assemblies e módulos desvinculados.</span><span class="sxs-lookup"><span data-stu-id="5d558-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="5d558-104">Esse método é como o [Método ImportFile](importfile-method.md), mas funciona mesmo que o arquivo que está sendo importado não exista no disco.</span><span class="sxs-lookup"><span data-stu-id="5d558-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d558-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d558-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="5d558-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5d558-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="5d558-107">Nome do arquivo a ser importado.</span><span class="sxs-lookup"><span data-stu-id="5d558-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="5d558-108">Nome de arquivo de saída opcional que pode ser usado para renomear o arquivo, pois ele está vinculado ao assembly.</span><span class="sxs-lookup"><span data-stu-id="5d558-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="5d558-109">Interface de [interface IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) de escopo opcional.</span><span class="sxs-lookup"><span data-stu-id="5d558-109">Optional scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="5d558-110">Se for TRUE, os irporttypes serão usados; caso contrário, a importação deverá ser executada manualmente.</span><span class="sxs-lookup"><span data-stu-id="5d558-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="5d558-111">Recebe a ID do arquivo ou assembly.</span><span class="sxs-lookup"><span data-stu-id="5d558-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="5d558-112">Recebe a interface de [interface IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5d558-112">Receives the [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="5d558-113">NULL se o arquivo não for um assembly.</span><span class="sxs-lookup"><span data-stu-id="5d558-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="5d558-114">Recebe a encontrada a partir de arquivos e/ou escopos importados.</span><span class="sxs-lookup"><span data-stu-id="5d558-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d558-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5d558-115">Return Value</span></span>  
 <span data-ttu-id="5d558-116">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="5d558-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d558-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d558-117">Requirements</span></span>  
 <span data-ttu-id="5d558-118">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="5d558-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d558-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d558-119">See also</span></span>

- [<span data-ttu-id="5d558-120">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="5d558-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5d558-121">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="5d558-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5d558-122">API do ALink</span><span class="sxs-lookup"><span data-stu-id="5d558-122">ALink API</span></span>](index.md)
