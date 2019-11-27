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
ms.openlocfilehash: 7e270dbfc63c03e77cb4b0694296e48c2035b8a6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445694"
---
# <a name="importfileex2-method"></a><span data-ttu-id="9e180-102">Método ImportFileEx2</span><span class="sxs-lookup"><span data-stu-id="9e180-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="9e180-103">Importa assemblies e módulos desvinculados.</span><span class="sxs-lookup"><span data-stu-id="9e180-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="9e180-104">Esse método é como o [Método ImportFile](importfile-method.md), mas funciona mesmo que o arquivo que está sendo importado não exista no disco.</span><span class="sxs-lookup"><span data-stu-id="9e180-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e180-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e180-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="9e180-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9e180-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="9e180-107">Nome do arquivo a ser importado.</span><span class="sxs-lookup"><span data-stu-id="9e180-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="9e180-108">Nome opcional do arquivo de destino.</span><span class="sxs-lookup"><span data-stu-id="9e180-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="9e180-109">Interface de [interface IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) de escopo de importação opcional.</span><span class="sxs-lookup"><span data-stu-id="9e180-109">Optional import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="9e180-110">Se for TRUE, os irporttypes serão usados; caso contrário, a importação deverá ser executada manualmente.</span><span class="sxs-lookup"><span data-stu-id="9e180-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="9e180-111">Sinalizadores a serem passados para o [método OpenScope](../metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="9e180-111">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="9e180-112">Recebe uma ID exclusiva para o assembly ou arquivo.</span><span class="sxs-lookup"><span data-stu-id="9e180-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="9e180-113">Recebe interface de [interface IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) de escopo de importação de assembly.</span><span class="sxs-lookup"><span data-stu-id="9e180-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="9e180-114">Poderá ser NULL se o arquivo não for um assembly.</span><span class="sxs-lookup"><span data-stu-id="9e180-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="9e180-115">Recebe o número de arquivos e/ou escopos importados.</span><span class="sxs-lookup"><span data-stu-id="9e180-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e180-116">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9e180-116">Return Value</span></span>  
 <span data-ttu-id="9e180-117">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="9e180-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e180-118">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9e180-118">Requirements</span></span>  
 <span data-ttu-id="9e180-119">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="9e180-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e180-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e180-120">See also</span></span>

- [<span data-ttu-id="9e180-121">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="9e180-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="9e180-122">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="9e180-122">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="9e180-123">API do ALink</span><span class="sxs-lookup"><span data-stu-id="9e180-123">ALink API</span></span>](index.md)
