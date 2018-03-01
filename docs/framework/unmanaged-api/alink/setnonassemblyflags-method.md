---
title: "Método SetNonAssemblyFlags"
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
- IALink.SetNonAssemblyFlags
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetNonAssemblyFlags
helpviewer_keywords:
- SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7e944f285ee0925b76fdd9b95c824deee38cead2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="16b52-102">Método SetNonAssemblyFlags</span><span class="sxs-lookup"><span data-stu-id="16b52-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="16b52-103">Define os sinalizadores que não são específicas do assembly.</span><span class="sxs-lookup"><span data-stu-id="16b52-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16b52-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16b52-104">Syntax</span></span>  
  
```  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16b52-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="16b52-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="16b52-106">Sinalizadores de ALink.</span><span class="sxs-lookup"><span data-stu-id="16b52-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16b52-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="16b52-107">Return Value</span></span>  
 <span data-ttu-id="16b52-108">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="16b52-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16b52-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="16b52-109">Requirements</span></span>  
 <span data-ttu-id="16b52-110">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="16b52-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16b52-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16b52-111">See Also</span></span>  
 [<span data-ttu-id="16b52-112">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="16b52-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="16b52-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="16b52-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="16b52-114">API do ALink</span><span class="sxs-lookup"><span data-stu-id="16b52-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
