---
title: Método ImportFileEx2
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx2
helpviewer_keywords:
- ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 784e58e0c5c2329705671580d53763f2ac30f0b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201345"
---
# <a name="importfileex2-method"></a><span data-ttu-id="5087a-102">Método ImportFileEx2</span><span class="sxs-lookup"><span data-stu-id="5087a-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="5087a-103">Importa os assemblies e módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="5087a-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="5087a-104">Esse método é como [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), mas funciona mesmo se o arquivo que está sendo importado não existe no disco.</span><span class="sxs-lookup"><span data-stu-id="5087a-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5087a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5087a-105">Syntax</span></span>  
  
```  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5087a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5087a-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="5087a-107">Nome do arquivo a ser importado.</span><span class="sxs-lookup"><span data-stu-id="5087a-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="5087a-108">Nome opcional do arquivo de destino.</span><span class="sxs-lookup"><span data-stu-id="5087a-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="5087a-109">Escopo de importação opcional [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="5087a-109">Optional import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="5087a-110">Se for TRUE, ImportTypes é usado, caso contrário, a importação deve ser executada manualmente.</span><span class="sxs-lookup"><span data-stu-id="5087a-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="5087a-111">Sinalizadores a serem passados para [método OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="5087a-111">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="5087a-112">Recebe a ID exclusiva para o arquivo ou assembly.</span><span class="sxs-lookup"><span data-stu-id="5087a-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="5087a-113">Recebe o escopo de importação de assembly [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="5087a-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="5087a-114">Pode ser NULL se o arquivo não é um assembly.</span><span class="sxs-lookup"><span data-stu-id="5087a-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="5087a-115">Recebe o número de arquivos e/ou importados de escopos.</span><span class="sxs-lookup"><span data-stu-id="5087a-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5087a-116">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5087a-116">Return Value</span></span>  
 <span data-ttu-id="5087a-117">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="5087a-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5087a-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5087a-118">Requirements</span></span>  
 <span data-ttu-id="5087a-119">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="5087a-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5087a-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5087a-120">See also</span></span>

- [<span data-ttu-id="5087a-121">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="5087a-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="5087a-122">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="5087a-122">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="5087a-123">API do ALink</span><span class="sxs-lookup"><span data-stu-id="5087a-123">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
