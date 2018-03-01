---
title: "Método ImportFileEx"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dc2af9db27c5194a1bdcef875b8db8d458d0edfe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="importfileex-method"></a><span data-ttu-id="7ff15-102">Método ImportFileEx</span><span class="sxs-lookup"><span data-stu-id="7ff15-102">ImportFileEx Method</span></span>
<span data-ttu-id="7ff15-103">Importações indicado assembly ou módulo não associado.</span><span class="sxs-lookup"><span data-stu-id="7ff15-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ff15-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ff15-104">Syntax</span></span>  
  
```  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ff15-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7ff15-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="7ff15-106">Nome totalmente qualificado do arquivo do qual importar.</span><span class="sxs-lookup"><span data-stu-id="7ff15-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="7ff15-107">Nome opcional do arquivo de destino.</span><span class="sxs-lookup"><span data-stu-id="7ff15-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="7ff15-108">Se TRUE, ImportTypes é usado, caso contrário, a importação deve ser executada manualmente.</span><span class="sxs-lookup"><span data-stu-id="7ff15-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="7ff15-109">Sinalizadores para ser passado para [método OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="7ff15-109">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="7ff15-110">Recebe o ID do arquivo que está sendo importado.</span><span class="sxs-lookup"><span data-stu-id="7ff15-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="7ff15-111">Recebe o escopo de importação de assembly [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="7ff15-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="7ff15-112">É definido como NULL se o arquivo não é um assembly.</span><span class="sxs-lookup"><span data-stu-id="7ff15-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="7ff15-113">Recebe a contagem de arquivos importados e/ou escopos.</span><span class="sxs-lookup"><span data-stu-id="7ff15-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ff15-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7ff15-114">Return Value</span></span>  
 <span data-ttu-id="7ff15-115">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="7ff15-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ff15-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7ff15-116">Requirements</span></span>  
 <span data-ttu-id="7ff15-117">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="7ff15-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff15-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ff15-118">See Also</span></span>  
 [<span data-ttu-id="7ff15-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="7ff15-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="7ff15-120">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="7ff15-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="7ff15-121">API do ALink</span><span class="sxs-lookup"><span data-stu-id="7ff15-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
