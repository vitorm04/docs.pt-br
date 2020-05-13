---
title: Método ICorDebugManagedCallback3::CustomNotification
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3.CustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type:
- apiref
ms.openlocfilehash: 8a4620e591cc80efb5c0fd53b0edf3a35849c421
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209754"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="83e06-102">Método ICorDebugManagedCallback3::CustomNotification</span><span class="sxs-lookup"><span data-stu-id="83e06-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="83e06-103">Indica que uma notificação de depurador personalizada foi gerada.</span><span class="sxs-lookup"><span data-stu-id="83e06-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83e06-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83e06-104">Syntax</span></span>  
  
```cpp  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83e06-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="83e06-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="83e06-106">no Um ponteiro para o thread que gerou a notificação.</span><span class="sxs-lookup"><span data-stu-id="83e06-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="83e06-107">no Um ponteiro para o domínio do aplicativo que contém o thread que gerou a notificação.</span><span class="sxs-lookup"><span data-stu-id="83e06-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83e06-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="83e06-108">Return Value</span></span>  
 <span data-ttu-id="83e06-109">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="83e06-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="83e06-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83e06-110">HRESULT</span></span>|<span data-ttu-id="83e06-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="83e06-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83e06-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="83e06-112">S_OK</span></span>|<span data-ttu-id="83e06-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="83e06-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="83e06-114">Exceções</span><span class="sxs-lookup"><span data-stu-id="83e06-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83e06-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="83e06-115">Remarks</span></span>  
 <span data-ttu-id="83e06-116">Uma chamada subsequente para o método [ICorDebugThread4:: GetCurrentCustomDebuggerNotification](icordebugthread4-getcurrentcustomdebuggernotification-method.md) recupera o objeto de thread que foi passado para o <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="83e06-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="83e06-117">O tipo do objeto de thread deve ter sido habilitado anteriormente chamando o método [ICorDebugProcess3:: SetEnableCustomNotification](icordebugprocess3-setenablecustomnotification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="83e06-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="83e06-118">O depurador pode ler parâmetros específicos de tipo dos campos do objeto de thread e pode armazenar respostas em campos.</span><span class="sxs-lookup"><span data-stu-id="83e06-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="83e06-119">A interface [ICorDebug](icordebug-interface.md) impõe nenhuma política sobre os tipos de notificações ou seu conteúdo, e a semântica das notificações é estritamente um contrato entre os depuradores, os aplicativos e a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="83e06-119">The [ICorDebug](icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83e06-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="83e06-120">Requirements</span></span>  
 <span data-ttu-id="83e06-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83e06-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83e06-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83e06-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83e06-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83e06-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83e06-124">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83e06-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e06-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="83e06-125">See also</span></span>

- [<span data-ttu-id="83e06-126">Interface ICorDebugManagedCallback3</span><span class="sxs-lookup"><span data-stu-id="83e06-126">ICorDebugManagedCallback3 Interface</span></span>](icordebugmanagedcallback3-interface.md)
- [<span data-ttu-id="83e06-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="83e06-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="83e06-128">Depuração</span><span class="sxs-lookup"><span data-stu-id="83e06-128">Debugging</span></span>](index.md)
