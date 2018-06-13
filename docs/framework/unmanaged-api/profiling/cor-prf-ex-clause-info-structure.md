---
title: Estrutura COR_PRF_EX_CLAUSE_INFO
ms.date: 03/30/2017
api_name:
- COR_PRF_EX_CLAUSE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords:
- COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3cf8b8735fc10b741d13b041eedc3e96607bef4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450109"
---
# <a name="corprfexclauseinfo-structure"></a>Estrutura COR_PRF_EX_CLAUSE_INFO
Armazena informações sobre uma instância de cláusula de exceção específica e seu quadro associado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`clauseType`|Um valor de [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeração que especifica o tipo de cláusula exceção o código que acabou de inserir ou à esquerda.|  
|`programCounter`|O ponto de entrada nativo do manipulador de cláusula — por exemplo, o conteúdo do registro X86 EIP.|  
|`framePointer`|O ponteiro para o quadro lógico para o manipulador de cláusula — por exemplo, o conteúdo do registro X86 EBP.|  
|`shadowStackPointer`|O ponteiro para a pilha de sombra. Esse valor é o conteúdo do registro BSP e só se aplica a IA64.|  
  
## <a name="remarks"></a>Comentários  
 Quando uma notificação de exceção é recebida, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) pode ser usado para obter as informações de endereço e o quadro nativo para a cláusula de exceção (`catch` / `finally`/filtro) que está prestes a ser executado ou executado anteriormente.  
  
 Esses retornos de chamada do common language runtime (CLR) envolve a execução de uma cláusula de exceção:  
  
-   [: Exceptioncatcherenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
-   [: Exceptionunwindfinallyenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
-   [: Exceptionsearchfilterenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
-   [Exceptioncatcherleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
-   [Exceptionunwindfinallyleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
-   [: Exceptionsearchfilterleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
