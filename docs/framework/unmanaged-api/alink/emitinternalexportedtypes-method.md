---
title: "Método EmitInternalExportedTypes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location: alink.dll
api_type: COM
f1_keywords: EmitInternalExportedTypes
helpviewer_keywords: EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f354058e0de944bbce9d128d3f4baa9b941fda08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="5f3c2-102">Método EmitInternalExportedTypes</span><span class="sxs-lookup"><span data-stu-id="5f3c2-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="5f3c2-103">Emite adicionados ao conjunto de tipos.</span><span class="sxs-lookup"><span data-stu-id="5f3c2-103">Emits types added to the assembly.</span></span> <span data-ttu-id="5f3c2-104">Chame este método depois conhecido tipos internos foram adicionados.</span><span class="sxs-lookup"><span data-stu-id="5f3c2-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f3c2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f3c2-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f3c2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5f3c2-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="5f3c2-107">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="5f3c2-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f3c2-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5f3c2-108">Return Value</span></span>  
 <span data-ttu-id="5f3c2-109">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="5f3c2-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f3c2-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5f3c2-110">Requirements</span></span>  
 <span data-ttu-id="5f3c2-111">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="5f3c2-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f3c2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f3c2-112">See Also</span></span>  
 [<span data-ttu-id="5f3c2-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="5f3c2-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="5f3c2-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="5f3c2-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="5f3c2-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="5f3c2-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
