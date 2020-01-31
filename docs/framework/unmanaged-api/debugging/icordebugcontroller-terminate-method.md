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
ms.openlocfilehash: 851a127c117b826c271dd021c41cfdb36045a1ff
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783749"
---
# <a name="icordebugcontrollerterminate-method"></a>Método ICorDebugController::Terminate
Encerra o processo com o código de saída especificado.  
  
> [!NOTE]
> Esse método é um wrapper para a função de `TerminateProcess` do Win32. Portanto, `Terminate` usa o código de saída da mesma maneira que a função de `TerminateProcess` do Win32 o utiliza.  
  
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
> Esse método não é implementado por um domínio de aplicativo. Ou seja, ele não é implementado no nível de <xref:System.AppDomain>.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também
