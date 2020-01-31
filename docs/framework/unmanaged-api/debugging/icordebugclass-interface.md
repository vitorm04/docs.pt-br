---
title: Interface ICorDebugClass
ms.date: 03/30/2017
api_name:
- ICorDebugClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass
helpviewer_keywords:
- ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type:
- apiref
ms.openlocfilehash: 7ac588591222a1abbc7b99ec7e973284c055f95e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784163"
---
# <a name="icordebugclass-interface"></a>Interface ICorDebugClass

Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário). Se o tipo for genérico, `ICorDebugClass` representará o tipo genérico sem instância.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetModule](icordebugclass-getmodule-method.md)|Obtém o módulo que define essa classe.|  
|[Método GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md)|Obtém o valor do campo estático especificado.|  
|[Método GetToken](icordebugclass-gettoken-method.md)|Obtém o token de metadados `TypeDef` para esta classe.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorDebugClass` representa um tipo genérico não instanciado. A interface ICorDebugType representa um tipo genérico instanciado. Por exemplo, `Hashtable<K, V>` seria representado por `ICorDebugClass`, enquanto `Hashtable<Int32, String>` seria representado por `ICorDebugType`.  
  
 Tipos não genéricos são representados por `ICorDebugClass` e `ICorDebugType`. A última interface foi introduzida no .NET Framework versão 2,0 para lidar com a instanciação de tipo.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
