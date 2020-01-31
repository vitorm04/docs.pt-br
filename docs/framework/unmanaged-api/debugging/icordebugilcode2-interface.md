---
title: Interface ICorDebugILCode2
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
ms.openlocfilehash: 30008d6cc98f7d0d0501d67e18703ed5a344d43a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794359"
---
# <a name="icordebugilcode2-interface"></a>Interface ICorDebugILCode2
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Estende logicamente a interface [ICorDebugILCode](icordebugilcode-interface.md) para fornecer métodos que retornam o token para a assinatura de variável local de uma função e que mapeiam os deslocamentos de Il (linguagem intermediária instrumentada) de um criador de perfil para os deslocamentos de Il do método original.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetInstrumentedILMap](icordebugilcode2-getinstrumentedilmap-method.md)|Retorna um mapa de deslocamentos da IL instrumentada do criador de perfil para os deslocamentos da IL do método original para esta instância.|  
|[Método GetLocalVarSigToken](icordebugilcode2-getlocalvarsigtoken-method.md)|Obtém o token de metadados para a assinatura de variável local para a função que é representada por esta instância.|  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugILCode](icordebugilcode-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
