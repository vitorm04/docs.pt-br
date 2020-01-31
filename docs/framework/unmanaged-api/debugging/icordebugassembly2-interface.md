---
title: Interface ICorDebugAssembly2
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2
helpviewer_keywords:
- ICorDebugAssembly2 interface [.NET Framework debugging]
ms.assetid: c0766e29-e573-4f9a-a928-167d1de5aa7e
topic_type:
- apiref
ms.openlocfilehash: 0a56a943efd43c1ace766669dea8747024b00917
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784691"
---
# <a name="icordebugassembly2-interface"></a>Interface ICorDebugAssembly2

Representa um assembly. Essa interface é uma extensão da interface ICorDebugAssembly.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método IsFullyTrusted](icordebugassembly2-isfullytrusted-method.md)|Obtém um valor que indica se o assembly recebeu confiança total pelo sistema de segurança de tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
