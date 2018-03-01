---
title: "Método ICorDebugFunction2::GetVersionNumber"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 16902d1a50f691ae555fdbc964bb9a1c6bf563c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction2getversionnumber-method"></a>Método ICorDebugFunction2::GetVersionNumber
Obtém a versão de editar e continuar dessa função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pnVersion`  
 [out] Um ponteiro para um inteiro que é o número de versão da função que é representado pelo objeto ICorDebugFunction2.  
  
## <a name="remarks"></a>Comentários  
 O tempo de execução mantém controle sobre o número de edições que foram executadas a cada módulo durante uma sessão de depuração. O número de versão de uma função é um mais do que o número da edição que introduziu a função. Versão original da função é a versão 1. O número é incrementado para um módulo sempre [Icordebugmodule2](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) é chamado em que o módulo. Portanto, se o corpo da função foi substituído na primeira e terceira chamada `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` pode retornar a versão 1, 2 ou 4 para essa função, mas não a versão 3. (Essa função não deve ter nenhuma versão 3).  
  
 O número de versão é controlado separadamente para cada módulo. Portanto, se você executar quatro edições no módulo 1 e nenhum no módulo 2, editar Avançar no módulo 1 atribuirá um número de versão de 6 para todas as funções editadas no módulo 1. Se o mesmo Editar ajustes módulo 2, as funções no módulo 2 obterá um número de versão de 2.  
  
 O número de versão é obtida com o `GetVersionNumber` método pode ser menor do que o obtido pela [Getcurrentversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).  
  
 O [Getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) método executa a mesma operação que `ICorDebugFunction2::GetVersionNumber`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
