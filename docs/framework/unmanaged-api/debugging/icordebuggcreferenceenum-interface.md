---
title: Interface ICorDebugGCReferenceEnum
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
ms.openlocfilehash: f01c27376191c3a2dddf56dae4b26c8b5193c73e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788650"
---
# <a name="icordebuggcreferenceenum-interface"></a>Interface ICorDebugGCReferenceEnum
Fornece um enumerador para objetos que serão coletados do lixo.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Next](icordebuggcreferenceenum-next-method.md)|Obtém o número especificado de instâncias de [COR_GC_REFERENCE](cor-gc-reference-structure.md) que contêm informações sobre objetos que serão coletados como lixo.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorDebugGCReferenceEnum` implementa a interface "ICorDebugEnum".  
  
 Uma instância de `ICorDebugGCReferenceEnum` é populada com instâncias de [COR_GC_REFERENCE](cor-gc-reference-structure.md) chamando o método [ICorDebugProcess5:: EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) . [COR_GC_REFERENCE](cor-gc-reference-structure.md) objetos podem ser enumerados chamando o método [ICorDebugGCReference:: Next](icordebuggcreferenceenum-next-method.md) .  
  
 Os objetos [COR_GC_REFERENCE](cor-gc-reference-structure.md) na coleção preenchida por esse método representam três tipos de objetos:  
  
- Objetos de todas as pilhas gerenciadas. Isso inclui referências dinâmicas em código gerenciado, bem como objetos criados pelo Common Language Runtime.  
  
- Objetos da tabela de identificadores. Isso inclui referências fortes (`HNDTYPE_STRONG` e `HNDTYPE_REFCOUNT`) e variáveis estáticas em um módulo.  
  
- Objetos da fila do finalizador. O finalizador enfileira objetos de raízes até que o finalizador tenha sido executado.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
