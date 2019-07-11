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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d76e9b4e18b46d0b546d6c66fa572c35cb9fcefe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741773"
---
# <a name="importfile-method"></a><span data-ttu-id="8dc8c-102">Método ImportFile</span><span class="sxs-lookup"><span data-stu-id="8dc8c-102">ImportFile Method</span></span>
<span data-ttu-id="8dc8c-103">Importa os assemblies e módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="8dc8c-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dc8c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8dc8c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8dc8c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8dc8c-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="8dc8c-106">Nome totalmente qualificado do arquivo a ser importado.</span><span class="sxs-lookup"><span data-stu-id="8dc8c-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="8dc8c-107">Nome de arquivo de saída opcional que pode ser usado para renomear o arquivo conforme ele é vinculado no assembly.</span><span class="sxs-lookup"><span data-stu-id="8dc8c-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="8dc8c-108">Se for TRUE, ImportTypes é usado, caso contrário, a importação deve ser executada manualmente.</span><span class="sxs-lookup"><span data-stu-id="8dc8c-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="8dc8c-109">Ponteiro para o token onde uma identificação exclusiva do arquivo será armazenada.</span><span class="sxs-lookup"><span data-stu-id="8dc8c-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="8dc8c-110">O arquivo pode ser um assembly ou um arquivo.</span><span class="sxs-lookup"><span data-stu-id="8dc8c-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="8dc8c-111">Recebe um ponteiro para [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8dc8c-111">Receives pointer to [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="8dc8c-112">Pode ser NULL se o arquivo não é um assembly.</span><span class="sxs-lookup"><span data-stu-id="8dc8c-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="8dc8c-113">Ponteiro para a contagem de arquivos e/ou escopos que foram importados.</span><span class="sxs-lookup"><span data-stu-id="8dc8c-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8dc8c-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8dc8c-114">Return Value</span></span>  
 <span data-ttu-id="8dc8c-115">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="8dc8c-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dc8c-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8dc8c-116">Requirements</span></span>  
 <span data-ttu-id="8dc8c-117">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="8dc8c-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dc8c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8dc8c-118">See also</span></span>

- [<span data-ttu-id="8dc8c-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="8dc8c-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="8dc8c-120">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="8dc8c-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="8dc8c-121">API do ALink</span><span class="sxs-lookup"><span data-stu-id="8dc8c-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
