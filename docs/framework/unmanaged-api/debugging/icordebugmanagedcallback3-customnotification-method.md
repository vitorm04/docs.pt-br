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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 098e140b7bffb7798a37b1881f2cb2ced36bcf1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416479"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="55f07-102">Método ICorDebugManagedCallback3::CustomNotification</span><span class="sxs-lookup"><span data-stu-id="55f07-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="55f07-103">Indica que uma notificação do depurador personalizados foi gerada.</span><span class="sxs-lookup"><span data-stu-id="55f07-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55f07-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55f07-104">Syntax</span></span>  
  
```  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55f07-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="55f07-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="55f07-106">[in] Um ponteiro para o thread que gerou a notificação.</span><span class="sxs-lookup"><span data-stu-id="55f07-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="55f07-107">[in] Um ponteiro para o domínio de aplicativo que contém o thread que gerou a notificação.</span><span class="sxs-lookup"><span data-stu-id="55f07-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55f07-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="55f07-108">Return Value</span></span>  
 <span data-ttu-id="55f07-109">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="55f07-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="55f07-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="55f07-110">HRESULT</span></span>|<span data-ttu-id="55f07-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="55f07-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="55f07-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="55f07-112">S_OK</span></span>|<span data-ttu-id="55f07-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="55f07-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="55f07-114">Exceções</span><span class="sxs-lookup"><span data-stu-id="55f07-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55f07-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="55f07-115">Remarks</span></span>  
 <span data-ttu-id="55f07-116">Uma chamada subsequente para a [Icordebugthread4](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) método recupera o objeto de thread que foi passado para o <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="55f07-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="55f07-117">Tipo de objeto de thread deve ter sido habilitado chamando o [Icordebugprocess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="55f07-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="55f07-118">O depurador pode ler parâmetros de tipo específico de campos do objeto de thread e pode armazenar as respostas nos campos.</span><span class="sxs-lookup"><span data-stu-id="55f07-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="55f07-119">O [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface não impõe nenhuma política nos tipos de notificações ou seu conteúdo e a semântica das notificações é estritamente um contrato entre os depuradores, aplicativos e o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55f07-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55f07-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="55f07-120">Requirements</span></span>  
 <span data-ttu-id="55f07-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55f07-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55f07-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55f07-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55f07-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55f07-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55f07-124">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55f07-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f07-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55f07-125">See Also</span></span>  
 [<span data-ttu-id="55f07-126">Interface ICorDebugManagedCallback3</span><span class="sxs-lookup"><span data-stu-id="55f07-126">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 [<span data-ttu-id="55f07-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="55f07-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="55f07-128">Depuração</span><span class="sxs-lookup"><span data-stu-id="55f07-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
