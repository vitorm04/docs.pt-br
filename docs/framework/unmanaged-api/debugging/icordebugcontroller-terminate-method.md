---
title: Método ICorDebugController::Terminate
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4c8dd8795fc3699176490ea0bb9b2e999038afb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749054"
---
# <a name="icordebugcontrollerterminate-method"></a>Método ICorDebugController::Terminate
Encerra o processo com o código de saída especificado.  
  
> [!NOTE]
>  Esse método é um wrapper do Win32 `TerminateProcess` função. Portanto, `Terminate` usa o código de saída da mesma forma que o Win32 `TerminateProcess` função utiliza.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `exitCode`  
 [in] Um valor numérico que é o código de saída. Os valores numéricos válidos são definidos em Winbase.  
  
## <a name="remarks"></a>Comentários  
 Se o processo é interrompido quando `Terminate` é chamado, o processo deve ser continuado, usando o [icordebugcontroller:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) método para que o depurador recebe uma confirmação do encerramento por meio do [ Icordebugmanagedcallback:: Exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) ou [icordebugmanagedcallback:: Exitappdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) retorno de chamada.  
  
> [!NOTE]
>  Este método não é implementado por um domínio do aplicativo. Ou seja, ele não está implementado de <xref:System.AppDomain> nível.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
