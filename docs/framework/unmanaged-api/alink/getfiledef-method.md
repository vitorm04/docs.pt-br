---
title: "Método GetFileDef"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.GetFileDef
api_location: alink.dll
api_type: COM
f1_keywords: GetFileDef
helpviewer_keywords: GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a31dee6bb1af4f555211822a3b7ec108353214a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="getfiledef-method"></a><span data-ttu-id="9ea96-102">Método GetFileDef</span><span class="sxs-lookup"><span data-stu-id="9ea96-102">GetFileDef Method</span></span>
<span data-ttu-id="9ea96-103">Recupera o token FileDef real usado nos metadados (em vez do token atribuído pelo ALink).</span><span class="sxs-lookup"><span data-stu-id="9ea96-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ea96-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ea96-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ea96-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9ea96-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9ea96-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="9ea96-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="9ea96-107">Token do arquivo adicionado, conforme recuperados do método AddFile ou método AddImport.</span><span class="sxs-lookup"><span data-stu-id="9ea96-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="9ea96-108">Recebe o token FileDef.</span><span class="sxs-lookup"><span data-stu-id="9ea96-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ea96-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9ea96-109">Return Value</span></span>  
 <span data-ttu-id="9ea96-110">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="9ea96-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ea96-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ea96-111">Requirements</span></span>  
 <span data-ttu-id="9ea96-112">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="9ea96-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ea96-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ea96-113">See Also</span></span>  
 [<span data-ttu-id="9ea96-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="9ea96-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="9ea96-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="9ea96-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="9ea96-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="9ea96-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
