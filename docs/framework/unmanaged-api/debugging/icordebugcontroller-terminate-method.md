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
ms.openlocfilehash: eade3fd5d946c44ae4a77c571f762709de3cef40
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976558"
---
# <a name="icordebugcontrollerterminate-method"></a>Método ICorDebugController::Terminate
Encerra o processo com o código de saída especificado.  
  
> [!NOTE]
> Esse método é um wrapper para a função `TerminateProcess` do Win32. Portanto, `Terminate` o usa o código de saída da mesma maneira que a `TerminateProcess` função do Win32 o utiliza.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `exitCode`  
 no Um valor numérico que é o código de saída. Os valores numéricos válidos são definidos em Winbase. h.  
  
## <a name="remarks"></a>Comentários  
 Se o processo for interrompido quando `Terminate` for chamado, o processo deverá continuar usando o método [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) para que o depurador receba a confirmação do encerramento por meio do retorno de chamada [ICorDebugManagedCallback:: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) ou [ICorDebugManagedCallback:: ExitAppDomain](icordebugmanagedcallback-exitappdomain-method.md) .  
  
> [!NOTE]
> Esse método não é implementado por um domínio de aplicativo. Ou seja, ele não é implementado no <xref:System.AppDomain> nível.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também
