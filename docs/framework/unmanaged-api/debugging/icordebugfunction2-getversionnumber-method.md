---
title: Método ICorDebugFunction2::GetVersionNumber
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cc9c2af62184c83857b82445941f6087a05c2c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995599"
---
# <a name="icordebugfunction2getversionnumber-method"></a>Método ICorDebugFunction2::GetVersionNumber
Obtém a versão de editar e continuar dessa função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pnVersion`  
 [out] Um ponteiro para um inteiro que é o número de versão da função que é representado por esse objeto ICorDebugFunction2.  
  
## <a name="remarks"></a>Comentários  
 O tempo de execução mantém controle sobre o número de edições que foram executadas para cada módulo durante uma sessão de depuração. O número de versão de uma função é um mais do que o número da edição que introduziu a função. Versão original da função é 1. O número é incrementado para um módulo sempre [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) é chamado no módulo. Portanto, se o corpo da função foi substituído na primeira e a terceira chamada para `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` pode retornar a versão 1, 2 ou 4 para essa função, mas não a versão 3. (Essa função não teria nenhuma versão 3).  
  
 O número de versão é controlado separadamente para cada módulo. Portanto, se você executar quatro edições no módulo 1 e nenhuma no módulo 2, sua próxima edição no módulo 1 atribuirá um número de versão de 6 para todas as funções editadas no módulo 1. Se o mesmo Editar toques módulo 2, as funções no módulo 2 obterá um número de versão 2.  
  
 O número de versão são obtidos com o `GetVersionNumber` método pode ser menor do que o obtido pela [ICorDebugFunction:: Getcurrentversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).  
  
 O [icordebugcode:: Getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) método executa a mesma operação que `ICorDebugFunction2::GetVersionNumber`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
