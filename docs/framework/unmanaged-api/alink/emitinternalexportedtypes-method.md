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
ms.openlocfilehash: 68373e9277a9d87bba6941259588f25a92af90a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710541"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="c55c7-102">Método EmitInternalExportedTypes</span><span class="sxs-lookup"><span data-stu-id="c55c7-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="c55c7-103">Emite tipos adicionados ao assembly.</span><span class="sxs-lookup"><span data-stu-id="c55c7-103">Emits types added to the assembly.</span></span> <span data-ttu-id="c55c7-104">Chame esse método depois conhecido tipos internos foram adicionados.</span><span class="sxs-lookup"><span data-stu-id="c55c7-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c55c7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c55c7-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c55c7-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c55c7-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c55c7-107">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="c55c7-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c55c7-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c55c7-108">Return Value</span></span>  
 <span data-ttu-id="c55c7-109">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="c55c7-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c55c7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c55c7-110">Requirements</span></span>  
 <span data-ttu-id="c55c7-111">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="c55c7-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c55c7-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c55c7-112">See also</span></span>
- [<span data-ttu-id="c55c7-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="c55c7-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c55c7-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="c55c7-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c55c7-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="c55c7-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
