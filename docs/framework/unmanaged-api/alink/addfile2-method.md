---
title: Método AddFile2
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a651be40773607e0db215eadf884ed642e6e3b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126926"
---
# <a name="addfile2-method"></a><span data-ttu-id="c0e00-102">Método AddFile2</span><span class="sxs-lookup"><span data-stu-id="c0e00-102">AddFile2 Method</span></span>
<span data-ttu-id="c0e00-103">Adiciona arquivos ao assembly.</span><span class="sxs-lookup"><span data-stu-id="c0e00-103">Adds files to the assembly.</span></span> <span data-ttu-id="c0e00-104">Também pode ser usado para criar os módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="c0e00-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0e00-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0e00-105">Syntax</span></span>  
  
```  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0e00-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c0e00-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c0e00-107">ID para o assembly ao qual o arquivo é adicionado.</span><span class="sxs-lookup"><span data-stu-id="c0e00-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="c0e00-108">Nome do arquivo a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="c0e00-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c0e00-109">COM+ `FileDef` sinaliza como `ffContainsNoMetaData` e `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="c0e00-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="c0e00-110">`dwFlags` é passado para [método DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="c0e00-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="c0e00-111">Interface [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="c0e00-111">Interface to [IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="c0e00-112">Recebe a ID para o arquivo que está sendo adicionado.</span><span class="sxs-lookup"><span data-stu-id="c0e00-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0e00-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c0e00-113">Return Value</span></span>  
 <span data-ttu-id="c0e00-114">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="c0e00-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0e00-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c0e00-115">Requirements</span></span>  
 <span data-ttu-id="c0e00-116">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="c0e00-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e00-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0e00-117">See also</span></span>

- [<span data-ttu-id="c0e00-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="c0e00-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c0e00-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="c0e00-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c0e00-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="c0e00-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
