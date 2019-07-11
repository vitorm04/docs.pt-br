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
ms.openlocfilehash: 18e0b7b3547bb246588f6b255483d4c317e0df88
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742235"
---
# <a name="closeassembly-method"></a><span data-ttu-id="34660-102">Método CloseAssembly</span><span class="sxs-lookup"><span data-stu-id="34660-102">CloseAssembly Method</span></span>
<span data-ttu-id="34660-103">Finaliza as operações de assembly.</span><span class="sxs-lookup"><span data-stu-id="34660-103">Finalizes assembly operations.</span></span> <span data-ttu-id="34660-104">Chame esse método antes de iniciar um novo assembly ou módulo não associado.</span><span class="sxs-lookup"><span data-stu-id="34660-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34660-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34660-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="34660-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34660-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="34660-107">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="34660-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34660-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="34660-108">Return Value</span></span>  
 <span data-ttu-id="34660-109">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="34660-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34660-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34660-110">Requirements</span></span>  
 <span data-ttu-id="34660-111">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="34660-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34660-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34660-112">See also</span></span>

- [<span data-ttu-id="34660-113">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="34660-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="34660-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="34660-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="34660-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="34660-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
