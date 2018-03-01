---
title: AddImport Method1
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
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d8827821deaeda311a42855737ecf53ab635a02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="addimport-method1"></a><span data-ttu-id="cfcab-102">AddImport Method1</span><span class="sxs-lookup"><span data-stu-id="cfcab-102">AddImport Method1</span></span>
<span data-ttu-id="cfcab-103">Adiciona o importa para o assembly.</span><span class="sxs-lookup"><span data-stu-id="cfcab-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfcab-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cfcab-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cfcab-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cfcab-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="cfcab-106">ID exclusiva do assembly a ser incrementado.</span><span class="sxs-lookup"><span data-stu-id="cfcab-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="cfcab-107">ID exclusiva, recuperado do [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), do arquivo a ser importado.</span><span class="sxs-lookup"><span data-stu-id="cfcab-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="cfcab-108">Sinalizadores de COM+ FileDef como `ffContainsNoMetaData` e `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="cfcab-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="cfcab-109">`dwFlags`é passado para [método DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="cfcab-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="cfcab-110">Ponteiro para o token que recebe a ID para o arquivo resultante.</span><span class="sxs-lookup"><span data-stu-id="cfcab-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfcab-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="cfcab-111">Return Value</span></span>  
 <span data-ttu-id="cfcab-112">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="cfcab-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfcab-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cfcab-113">Requirements</span></span>  
 <span data-ttu-id="cfcab-114">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="cfcab-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfcab-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfcab-115">See Also</span></span>  
 [<span data-ttu-id="cfcab-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="cfcab-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="cfcab-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="cfcab-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="cfcab-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="cfcab-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
