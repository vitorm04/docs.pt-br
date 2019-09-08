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
ms.openlocfilehash: b7828c86018724bb934de99cab4617f9885fdca6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787611"
---
# <a name="closeassembly-method"></a><span data-ttu-id="4d99b-102">Método CloseAssembly</span><span class="sxs-lookup"><span data-stu-id="4d99b-102">CloseAssembly Method</span></span>
<span data-ttu-id="4d99b-103">Finaliza operações de assembly.</span><span class="sxs-lookup"><span data-stu-id="4d99b-103">Finalizes assembly operations.</span></span> <span data-ttu-id="4d99b-104">Chame esse método antes de iniciar um novo assembly ou módulo não associado.</span><span class="sxs-lookup"><span data-stu-id="4d99b-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d99b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d99b-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d99b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4d99b-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4d99b-107">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="4d99b-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d99b-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4d99b-108">Return Value</span></span>  
 <span data-ttu-id="4d99b-109">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="4d99b-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d99b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4d99b-110">Requirements</span></span>  
 <span data-ttu-id="4d99b-111">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="4d99b-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d99b-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d99b-112">See also</span></span>

- [<span data-ttu-id="4d99b-113">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="4d99b-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4d99b-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="4d99b-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4d99b-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="4d99b-115">ALink API</span></span>](index.md)
