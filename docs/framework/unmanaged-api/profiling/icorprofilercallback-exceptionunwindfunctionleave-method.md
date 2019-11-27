---
title: Método ICorProfilerCallback::ExceptionUnwindFunctionLeave
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
ms.openlocfilehash: 645c9dd9319dfdf9cb070366d2c389f879e1b1d2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448052"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a>Método ICorProfilerCallback::ExceptionUnwindFunctionLeave
Notifica o criador de perfil de que a fase de desenrolamento da manipulação de exceções concluiu o desenrolamento de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a>Comentários  
 Quando o método de `ExceptionUnwindFunctionLeave` é chamado, a instância de função e seus dados de pilha são removidos da pilha.  
  
 O criador de perfil não deve bloquear durante essa chamada porque a pilha pode não estar em um estado que permita a coleta de lixo e, portanto, a coleta de lixo preemptiva não pode ser habilitada. Se o criador de perfil for bloqueado aqui e uma tentativa de coleta de lixo, o tempo de execução será bloqueado até que esse retorno de chamada seja retornado.  
  
 Além disso, durante essa chamada, o criador de perfil não deve chamar o código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Método ExceptionUnwindFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)
