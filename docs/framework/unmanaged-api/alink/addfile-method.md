---
title: AddFile Method1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.AddFile
- AddFile
api_location: alink.dll
api_type: COM
f1_keywords: AddFile
helpviewer_keywords: AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9463f2c41f56287ebfc4fb55aa8208c37522a57f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="addfile-method1"></a><span data-ttu-id="dd993-102">AddFile Method1</span><span class="sxs-lookup"><span data-stu-id="dd993-102">AddFile Method1</span></span>
<span data-ttu-id="dd993-103">Adiciona arquivos ao assembly.</span><span class="sxs-lookup"><span data-stu-id="dd993-103">Adds files to the assembly.</span></span> <span data-ttu-id="dd993-104">Também pode ser usado para criar os módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="dd993-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd993-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd993-105">Syntax</span></span>  
  
```  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd993-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dd993-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="dd993-107">ID exclusiva do assembly deve ser aumentado.</span><span class="sxs-lookup"><span data-stu-id="dd993-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="dd993-108">Nome totalmente qualificado do arquivo a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="dd993-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="dd993-109">Sinalizadores de COM+ FileDef como `ffContainsNoMetaData` e `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="dd993-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="dd993-110">`dwFlags`é passado para [método DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="dd993-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="dd993-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface a ser usado para emitir metadados, se necessário.</span><span class="sxs-lookup"><span data-stu-id="dd993-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="dd993-112">Ponteiro para onde a ID exclusiva do arquivo adicionado será armazenada.</span><span class="sxs-lookup"><span data-stu-id="dd993-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd993-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="dd993-113">Return Value</span></span>  
 <span data-ttu-id="dd993-114">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="dd993-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd993-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dd993-115">Requirements</span></span>  
 <span data-ttu-id="dd993-116">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="dd993-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd993-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd993-117">See Also</span></span>  
 [<span data-ttu-id="dd993-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="dd993-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="dd993-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="dd993-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="dd993-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="dd993-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
