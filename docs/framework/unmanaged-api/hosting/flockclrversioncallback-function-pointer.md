---
title: Ponteiro de função FLockClrVersionCallback
ms.date: 03/30/2017
api_name:
- FLockClrVersionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FLockClrVersionCallback
helpviewer_keywords:
- FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type:
- apiref
ms.openlocfilehash: af42de820b2d835e8ea137a2643a51678e382ff0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617276"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="bb6f9-102">Ponteiro de função FLockClrVersionCallback</span><span class="sxs-lookup"><span data-stu-id="bb6f9-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="bb6f9-103">Aponta para uma função que o Common Language Runtime (CLR) chama para indicar que a inicialização foi iniciada ou concluída.</span><span class="sxs-lookup"><span data-stu-id="bb6f9-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="bb6f9-104">Esse ponteiro de função foi preterido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="bb6f9-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb6f9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb6f9-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="bb6f9-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb6f9-106">Remarks</span></span>  
 <span data-ttu-id="bb6f9-107">Essa função é implementada pelo host.</span><span class="sxs-lookup"><span data-stu-id="bb6f9-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb6f9-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bb6f9-108">Requirements</span></span>  
 <span data-ttu-id="bb6f9-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb6f9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb6f9-110">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bb6f9-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb6f9-111">**Biblioteca:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="bb6f9-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="bb6f9-112">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb6f9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb6f9-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="bb6f9-113">See also</span></span>

- [<span data-ttu-id="bb6f9-114">Função LockClrVersion</span><span class="sxs-lookup"><span data-stu-id="bb6f9-114">LockClrVersion Function</span></span>](lockclrversion-function.md)
- [<span data-ttu-id="bb6f9-115">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="bb6f9-115">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
