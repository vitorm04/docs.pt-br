---
title: "Método AddFile2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- AddFile2
- IALink2.AddFile2
api_location: alink.dll
api_type: COM
f1_keywords: AddFile2
helpviewer_keywords: AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fe10a3ca8930087a52d02905534696dbb2d8fb25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="addfile2-method"></a><span data-ttu-id="cd45b-102">Método AddFile2</span><span class="sxs-lookup"><span data-stu-id="cd45b-102">AddFile2 Method</span></span>
<span data-ttu-id="cd45b-103">Adiciona arquivos ao assembly.</span><span class="sxs-lookup"><span data-stu-id="cd45b-103">Adds files to the assembly.</span></span> <span data-ttu-id="cd45b-104">Também pode ser usado para criar os módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="cd45b-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd45b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd45b-105">Syntax</span></span>  
  
```  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd45b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cd45b-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="cd45b-107">ID do assembly para o qual o arquivo é adicionado.</span><span class="sxs-lookup"><span data-stu-id="cd45b-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="cd45b-108">Nome do arquivo a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="cd45b-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="cd45b-109">COM+ `FileDef` sinalizadores como `ffContainsNoMetaData` e `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="cd45b-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="cd45b-110">`dwFlags`é passado para [método DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="cd45b-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="cd45b-111">Interface [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="cd45b-111">Interface to [IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="cd45b-112">Recebe o ID do arquivo que está sendo adicionado.</span><span class="sxs-lookup"><span data-stu-id="cd45b-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd45b-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="cd45b-113">Return Value</span></span>  
 <span data-ttu-id="cd45b-114">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="cd45b-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd45b-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cd45b-115">Requirements</span></span>  
 <span data-ttu-id="cd45b-116">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="cd45b-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd45b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd45b-117">See Also</span></span>  
 [<span data-ttu-id="cd45b-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="cd45b-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="cd45b-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="cd45b-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="cd45b-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="cd45b-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
