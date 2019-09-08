---
title: Método SetNonAssemblyFlags
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8a22e958740b69ba0e09bf062bf4d86075c3ff1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777017"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="9db15-102">Método SetNonAssemblyFlags</span><span class="sxs-lookup"><span data-stu-id="9db15-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="9db15-103">Define sinalizadores que não são específicos do assembly.</span><span class="sxs-lookup"><span data-stu-id="9db15-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9db15-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9db15-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9db15-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9db15-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="9db15-106">Sinalizadores ALink.</span><span class="sxs-lookup"><span data-stu-id="9db15-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9db15-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9db15-107">Return Value</span></span>  
 <span data-ttu-id="9db15-108">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="9db15-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9db15-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9db15-109">Requirements</span></span>  
 <span data-ttu-id="9db15-110">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="9db15-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9db15-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9db15-111">See also</span></span>

- [<span data-ttu-id="9db15-112">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="9db15-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="9db15-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="9db15-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="9db15-114">API do ALink</span><span class="sxs-lookup"><span data-stu-id="9db15-114">ALink API</span></span>](index.md)
