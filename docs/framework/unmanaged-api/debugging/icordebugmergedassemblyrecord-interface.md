---
title: Interface ICorDebugMergedAssemblyRecord
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: 6d5d862110cd91e8ac81c96e50486be10c579903
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793064"
---
# <a name="icordebugmergedassemblyrecord-interface"></a>Interface ICorDebugMergedAssemblyRecord
Fornece informações sobre um assembly mesclado.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetCulture](icordebugmergedassemblyrecord-getculture-method.md)|Obtém a cadeia de caracteres do nome da cultura do assembly.|  
|[Método GetIndex](icordebugmergedassemblyrecord-getindex-method.md)|Obtém o índice de prefixo do assembly.|  
|[Método GetPublicKey](icordebugmergedassemblyrecord-getpublickey-method.md)|Obtém a chave pública do assembly.|  
|[Método GetPublicKeyToken](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|Obtém o token de chave pública do assembly.|  
|[Método GetSimpleName](icordebugmergedassemblyrecord-getsimplename-method.md)|Obtém o nome simples do assembly.|  
|[Método GetVersion](icordebugmergedassemblyrecord-getversion-method.md)|Obtém as informações de versão do assembly.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Essa interface está disponível somente com .NET Native. Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
