---
title: Método ImportFile
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
ms.openlocfilehash: cda6d90865f8ad2b9d565f6a6378c35b03c65bf7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446997"
---
# <a name="importfile-method"></a><span data-ttu-id="284d3-102">Método ImportFile</span><span class="sxs-lookup"><span data-stu-id="284d3-102">ImportFile Method</span></span>
<span data-ttu-id="284d3-103">Importa assemblies e módulos desvinculados.</span><span class="sxs-lookup"><span data-stu-id="284d3-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="284d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="284d3-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="284d3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="284d3-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="284d3-106">Nome totalmente qualificado do arquivo a ser importado.</span><span class="sxs-lookup"><span data-stu-id="284d3-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="284d3-107">Nome de arquivo de saída opcional que pode ser usado para renomear o arquivo, pois ele está vinculado ao assembly.</span><span class="sxs-lookup"><span data-stu-id="284d3-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="284d3-108">Se for TRUE, os irporttypes serão usados; caso contrário, a importação deverá ser executada manualmente.</span><span class="sxs-lookup"><span data-stu-id="284d3-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="284d3-109">Ponteiro para o token em que uma ID de arquivo exclusiva será armazenada.</span><span class="sxs-lookup"><span data-stu-id="284d3-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="284d3-110">O arquivo pode ser um assembly ou um arquivo.</span><span class="sxs-lookup"><span data-stu-id="284d3-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="284d3-111">Recebe o ponteiro para a [interface IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md).</span><span class="sxs-lookup"><span data-stu-id="284d3-111">Receives pointer to [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="284d3-112">Poderá ser NULL se o arquivo não for um assembly.</span><span class="sxs-lookup"><span data-stu-id="284d3-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="284d3-113">Ponteiro para a contagem de arquivos e/ou escopos que foram importados.</span><span class="sxs-lookup"><span data-stu-id="284d3-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="284d3-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="284d3-114">Return Value</span></span>  
 <span data-ttu-id="284d3-115">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="284d3-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="284d3-116">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="284d3-116">Requirements</span></span>  
 <span data-ttu-id="284d3-117">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="284d3-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="284d3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="284d3-118">See also</span></span>

- [<span data-ttu-id="284d3-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="284d3-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="284d3-120">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="284d3-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="284d3-121">API do ALink</span><span class="sxs-lookup"><span data-stu-id="284d3-121">ALink API</span></span>](index.md)
