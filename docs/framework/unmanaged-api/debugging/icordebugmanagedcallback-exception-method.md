---
title: Método ICorDebugManagedCallback::Exception
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
ms.openlocfilehash: 2d0461709accf1a9300c072b62bd58734cb33fb8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209806"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="42662-102">Método ICorDebugManagedCallback::Exception</span><span class="sxs-lookup"><span data-stu-id="42662-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="42662-103">Notifica o depurador de que uma exceção foi lançada do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="42662-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42662-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42662-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42662-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="42662-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="42662-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo no qual a exceção foi gerada.</span><span class="sxs-lookup"><span data-stu-id="42662-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="42662-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread no qual a exceção foi gerada.</span><span class="sxs-lookup"><span data-stu-id="42662-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="42662-108">no Se esse valor for `false` , a exceção ainda não foi processada pelo aplicativo; caso contrário, a exceção será sem tratamento e encerrará o processo.</span><span class="sxs-lookup"><span data-stu-id="42662-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42662-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="42662-109">Remarks</span></span>  
 <span data-ttu-id="42662-110">A exceção específica pode ser recuperada do objeto de thread.</span><span class="sxs-lookup"><span data-stu-id="42662-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42662-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="42662-111">Requirements</span></span>  
 <span data-ttu-id="42662-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42662-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42662-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42662-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42662-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42662-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42662-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42662-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42662-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="42662-116">See also</span></span>

- [<span data-ttu-id="42662-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="42662-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
