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
ms.openlocfilehash: 70dca19075d8c896408ec78f89549b0c539280de
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446573"
---
# <a name="closeassembly-method"></a><span data-ttu-id="d9305-102">Método CloseAssembly</span><span class="sxs-lookup"><span data-stu-id="d9305-102">CloseAssembly Method</span></span>
<span data-ttu-id="d9305-103">Finaliza operações de assembly.</span><span class="sxs-lookup"><span data-stu-id="d9305-103">Finalizes assembly operations.</span></span> <span data-ttu-id="d9305-104">Chame esse método antes de iniciar um novo assembly ou módulo não associado.</span><span class="sxs-lookup"><span data-stu-id="d9305-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9305-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9305-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9305-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d9305-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d9305-107">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="d9305-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9305-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d9305-108">Return Value</span></span>  
 <span data-ttu-id="d9305-109">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="d9305-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9305-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9305-110">Requirements</span></span>  
 <span data-ttu-id="d9305-111">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="d9305-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9305-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9305-112">See also</span></span>

- [<span data-ttu-id="d9305-113">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="d9305-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d9305-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="d9305-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d9305-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="d9305-115">ALink API</span></span>](index.md)
