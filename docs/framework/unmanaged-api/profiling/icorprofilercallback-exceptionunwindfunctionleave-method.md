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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a79a9c925392b0ab5e50269479b2f693f1a9b58d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a>Método ICorProfilerCallback::ExceptionUnwindFunctionLeave
Notifica o criador de perfil que a fase de desenrolamento de tratamento de exceção concluiu a liberação de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a>Comentários  
 Quando o `ExceptionUnwindFunctionLeave` método é chamado, a instância de função e seus dados de pilha são removidos da pilha.  
  
 O criador de perfil não deve bloquear durante esta chamada porque a pilha não pode estar em um estado que permite a coleta de lixo e, portanto, a coleta de lixo preemptivo não pode ser habilitada. Se você tentar aqui os blocos do criador de perfil e uma coleta de lixo, tempo de execução será bloqueado até que esse retorno de chamada retorna.  
  
 Além disso, durante essa chamada, o criador de perfil não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Método ExceptionUnwindFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)
