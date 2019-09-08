---
title: Método ImportFileEx
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd138d0418bb9667a86419d719bf0b95a4bb1b12
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777120"
---
# <a name="importfileex-method"></a><span data-ttu-id="520ea-102">Método ImportFileEx</span><span class="sxs-lookup"><span data-stu-id="520ea-102">ImportFileEx Method</span></span>
<span data-ttu-id="520ea-103">Importações indicadas módulo de assembly ou não associado.</span><span class="sxs-lookup"><span data-stu-id="520ea-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="520ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="520ea-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="520ea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="520ea-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="520ea-106">Nome totalmente qualificado do arquivo do qual importar.</span><span class="sxs-lookup"><span data-stu-id="520ea-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="520ea-107">Nome opcional do arquivo de destino.</span><span class="sxs-lookup"><span data-stu-id="520ea-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="520ea-108">Se for TRUE, os irporttypes serão usados; caso contrário, a importação deverá ser executada manualmente.</span><span class="sxs-lookup"><span data-stu-id="520ea-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="520ea-109">Sinalizadores a serem passados para o [método OpenScope](../metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="520ea-109">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="520ea-110">Recebe a ID do arquivo que está sendo importado.</span><span class="sxs-lookup"><span data-stu-id="520ea-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="520ea-111">Recebe interface de [interface IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) de escopo de importação de assembly.</span><span class="sxs-lookup"><span data-stu-id="520ea-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="520ea-112">Será definido como NULL se o arquivo não for um assembly.</span><span class="sxs-lookup"><span data-stu-id="520ea-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="520ea-113">Recebe a contagem de escopos e/ou arquivos importados.</span><span class="sxs-lookup"><span data-stu-id="520ea-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="520ea-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="520ea-114">Return Value</span></span>  
 <span data-ttu-id="520ea-115">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="520ea-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="520ea-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="520ea-116">Requirements</span></span>  
 <span data-ttu-id="520ea-117">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="520ea-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="520ea-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="520ea-118">See also</span></span>

- [<span data-ttu-id="520ea-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="520ea-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="520ea-120">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="520ea-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="520ea-121">API do ALink</span><span class="sxs-lookup"><span data-stu-id="520ea-121">ALink API</span></span>](index.md)
