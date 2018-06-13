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
ms.openlocfilehash: be6332c76b3dae9c02e1a939286b70438ee14cfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400673"
---
# <a name="importfileex2-method"></a><span data-ttu-id="7a491-102">Método ImportFileEx2</span><span class="sxs-lookup"><span data-stu-id="7a491-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="7a491-103">Importa os assemblies e módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="7a491-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="7a491-104">Esse método é como [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), mas funciona mesmo se o arquivo que está sendo importado não existe no disco.</span><span class="sxs-lookup"><span data-stu-id="7a491-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a491-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a491-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="7a491-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7a491-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="7a491-107">Nome do arquivo a ser importado.</span><span class="sxs-lookup"><span data-stu-id="7a491-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="7a491-108">Nome opcional do arquivo de destino.</span><span class="sxs-lookup"><span data-stu-id="7a491-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="7a491-109">Escopo de importação opcional [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="7a491-109">Optional import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="7a491-110">Se TRUE, ImportTypes é usado, caso contrário, a importação deve ser executada manualmente.</span><span class="sxs-lookup"><span data-stu-id="7a491-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="7a491-111">Sinalizadores para ser passado para [método OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="7a491-111">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="7a491-112">Recebe uma ID exclusiva para o assembly ou arquivo.</span><span class="sxs-lookup"><span data-stu-id="7a491-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="7a491-113">Recebe o escopo de importação de assembly [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="7a491-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="7a491-114">Pode ser NULL se o arquivo não é um assembly.</span><span class="sxs-lookup"><span data-stu-id="7a491-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="7a491-115">Recebe o número de arquivos e/ou importados de escopos.</span><span class="sxs-lookup"><span data-stu-id="7a491-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a491-116">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7a491-116">Return Value</span></span>  
 <span data-ttu-id="7a491-117">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="7a491-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a491-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a491-118">Requirements</span></span>  
 <span data-ttu-id="7a491-119">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="7a491-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a491-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a491-120">See Also</span></span>  
 [<span data-ttu-id="7a491-121">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="7a491-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="7a491-122">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="7a491-122">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="7a491-123">API do ALink</span><span class="sxs-lookup"><span data-stu-id="7a491-123">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
