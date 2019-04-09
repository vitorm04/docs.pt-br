---
title: Método CloseAssembly
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 94c1c083d010cd82fd9e9e2f02b23e81d88fedd5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116435"
---
# <a name="closeassembly-method"></a><span data-ttu-id="c512f-102">Método CloseAssembly</span><span class="sxs-lookup"><span data-stu-id="c512f-102">CloseAssembly Method</span></span>
<span data-ttu-id="c512f-103">Finaliza as operações de assembly.</span><span class="sxs-lookup"><span data-stu-id="c512f-103">Finalizes assembly operations.</span></span> <span data-ttu-id="c512f-104">Chame esse método antes de iniciar um novo assembly ou módulo não associado.</span><span class="sxs-lookup"><span data-stu-id="c512f-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c512f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c512f-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c512f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c512f-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c512f-107">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="c512f-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c512f-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c512f-108">Return Value</span></span>  
 <span data-ttu-id="c512f-109">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="c512f-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c512f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c512f-110">Requirements</span></span>  
 <span data-ttu-id="c512f-111">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="c512f-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c512f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c512f-112">See also</span></span>

- [<span data-ttu-id="c512f-113">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="c512f-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c512f-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="c512f-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c512f-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="c512f-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
