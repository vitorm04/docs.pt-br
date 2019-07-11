---
title: Método EmitInternalExportedTypes
ms.date: 03/30/2017
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitInternalExportedTypes
helpviewer_keywords:
- EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15174480c4345f2514572701a5525f0f192ad120
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742093"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="3fd3c-102">Método EmitInternalExportedTypes</span><span class="sxs-lookup"><span data-stu-id="3fd3c-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="3fd3c-103">Emite tipos adicionados ao assembly.</span><span class="sxs-lookup"><span data-stu-id="3fd3c-103">Emits types added to the assembly.</span></span> <span data-ttu-id="3fd3c-104">Chame esse método depois conhecido tipos internos foram adicionados.</span><span class="sxs-lookup"><span data-stu-id="3fd3c-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fd3c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3fd3c-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fd3c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3fd3c-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3fd3c-107">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="3fd3c-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fd3c-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3fd3c-108">Return Value</span></span>  
 <span data-ttu-id="3fd3c-109">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="3fd3c-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fd3c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3fd3c-110">Requirements</span></span>  
 <span data-ttu-id="3fd3c-111">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="3fd3c-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd3c-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3fd3c-112">See also</span></span>

- [<span data-ttu-id="3fd3c-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="3fd3c-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="3fd3c-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="3fd3c-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="3fd3c-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="3fd3c-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
