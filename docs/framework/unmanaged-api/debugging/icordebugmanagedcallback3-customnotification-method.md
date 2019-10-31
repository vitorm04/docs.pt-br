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
ms.openlocfilehash: 83192fd2d24e740ab470988531db823b34df4494
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131432"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="a9274-102">Método ICorDebugManagedCallback3::CustomNotification</span><span class="sxs-lookup"><span data-stu-id="a9274-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="a9274-103">Indica que uma notificação de depurador personalizada foi gerada.</span><span class="sxs-lookup"><span data-stu-id="a9274-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9274-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9274-104">Syntax</span></span>  
  
```cpp  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9274-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a9274-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="a9274-106">no Um ponteiro para o thread que gerou a notificação.</span><span class="sxs-lookup"><span data-stu-id="a9274-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="a9274-107">no Um ponteiro para o domínio do aplicativo que contém o thread que gerou a notificação.</span><span class="sxs-lookup"><span data-stu-id="a9274-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9274-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a9274-108">Return Value</span></span>  
 <span data-ttu-id="a9274-109">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="a9274-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a9274-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9274-110">HRESULT</span></span>|<span data-ttu-id="a9274-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9274-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9274-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9274-112">S_OK</span></span>|<span data-ttu-id="a9274-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="a9274-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="a9274-114">Exceções</span><span class="sxs-lookup"><span data-stu-id="a9274-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9274-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="a9274-115">Remarks</span></span>  
 <span data-ttu-id="a9274-116">Uma chamada subsequente para o método [ICorDebugThread4:: GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) recupera o objeto de thread que foi passado para o método <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a9274-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a9274-117">O tipo do objeto de thread deve ter sido habilitado anteriormente chamando o método [ICorDebugProcess3:: SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a9274-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="a9274-118">O depurador pode ler parâmetros específicos de tipo dos campos do objeto de thread e pode armazenar respostas em campos.</span><span class="sxs-lookup"><span data-stu-id="a9274-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="a9274-119">A interface [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) impõe nenhuma política sobre os tipos de notificações ou seu conteúdo, e a semântica das notificações é estritamente um contrato entre os depuradores, os aplicativos e a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a9274-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9274-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a9274-120">Requirements</span></span>  
 <span data-ttu-id="a9274-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9274-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9274-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9274-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9274-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9274-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9274-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9274-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9274-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9274-125">See also</span></span>

- [<span data-ttu-id="a9274-126">Interface ICorDebugManagedCallback3</span><span class="sxs-lookup"><span data-stu-id="a9274-126">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)
- [<span data-ttu-id="a9274-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a9274-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a9274-128">Depuração</span><span class="sxs-lookup"><span data-stu-id="a9274-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
