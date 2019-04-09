---
title: Método ICorDebugDebugEvent::GetThread
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 103768918f67ca695a47c52b9cd97f24fb8d46ce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081566"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="a39cc-102">Método ICorDebugDebugEvent::GetThread</span><span class="sxs-lookup"><span data-stu-id="a39cc-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="a39cc-103">Obtém o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="a39cc-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a39cc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a39cc-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a39cc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a39cc-105">Parameters</span></span>  
 <span data-ttu-id="a39cc-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="a39cc-106">ppThread</span></span>  
 <span data-ttu-id="a39cc-107">[out] Um ponteiro para o endereço de um objeto de ICorDebugThread que representa o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="a39cc-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a39cc-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a39cc-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a39cc-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a39cc-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a39cc-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a39cc-110">Requirements</span></span>  
 <span data-ttu-id="a39cc-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a39cc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a39cc-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a39cc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a39cc-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a39cc-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a39cc-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a39cc-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a39cc-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a39cc-115">See also</span></span>

- [<span data-ttu-id="a39cc-116">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="a39cc-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="a39cc-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a39cc-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
