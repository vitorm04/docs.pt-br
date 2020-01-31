---
title: Interface ICorDebugFunction3
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
ms.openlocfilehash: 7ef983c2f0785cb97baf8ba1ad3483b46c08af9a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788651"
---
# <a name="icordebugfunction3-interface"></a>Interface ICorDebugFunction3
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Estende a interface de ICorDebugFunction logicamente para fornecer acesso ao código a partir de uma solicitação ReJIT.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetActiveReJitRequestILCode](icordebugfunction3-getactiverejitrequestilcode-method.md)|Obtém um ponteiro de interface para um [ICorDebugILCode](icordebugilcode-interface.md) que contém o Il de uma solicitação de ReJIT ativa.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
- [ReJIT: um guia de instruções](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
