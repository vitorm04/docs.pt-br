---
title: "Método EmitAssembly"
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
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f012ea89fec0e64bc1639e6c47fb79249c25411a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="emitassembly-method"></a><span data-ttu-id="c11e3-102">Método EmitAssembly</span><span class="sxs-lookup"><span data-stu-id="c11e3-102">EmitAssembly Method</span></span>
<span data-ttu-id="c11e3-103">Cria o assembly.</span><span class="sxs-lookup"><span data-stu-id="c11e3-103">Creates the assembly.</span></span> <span data-ttu-id="c11e3-104">Chame este método depois que todos os outros arquivos são fechados, exceto o arquivo de assembly.</span><span class="sxs-lookup"><span data-stu-id="c11e3-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="c11e3-105">Não chame este método durante a produção de módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="c11e3-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c11e3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c11e3-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c11e3-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c11e3-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c11e3-108">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="c11e3-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c11e3-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c11e3-109">Return Value</span></span>  
 <span data-ttu-id="c11e3-110">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="c11e3-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c11e3-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c11e3-111">Requirements</span></span>  
 <span data-ttu-id="c11e3-112">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="c11e3-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c11e3-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c11e3-113">See Also</span></span>  
 [<span data-ttu-id="c11e3-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="c11e3-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="c11e3-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="c11e3-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="c11e3-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="c11e3-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
