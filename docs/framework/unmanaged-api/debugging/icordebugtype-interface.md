---
title: Interface ICorDebugType
ms.date: 03/30/2017
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
ms.openlocfilehash: 5e88652ff75223e30e6abc454f1e1af91494c7b2
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396698"
---
# <a name="icordebugtype-interface"></a>Interface ICorDebugType
Representa um tipo, básico ou complexo (ou seja, definido pelo usuário). Se o tipo for genérico, `ICorDebugType` representará o tipo genérico instanciado.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumerateTypeParameters](icordebugtype-enumeratetypeparameters-method.md)|Obtém um ponteiro de interface para um ICorDebugTypeEnum que faz referência aos <xref:System.Type> parâmetros genéricos da classe referenciada por isso `ICorDebugType` .|  
|[Método GetBase](icordebugtype-getbase-method.md)|Obtém um ponteiro de interface para um `ICorDebugType` que faz referência à classe base da classe referenciada por isso `ICorDebugType` , se houver.|  
|[Método GetClass](icordebugtype-getclass-method.md)|Obtém um ponteiro de interface para um ICorDebugClass que faz referência ao Construtor tipado deste `ICorDebugType` .|  
|[Método GetFirstTypeParameter](icordebugtype-getfirsttypeparameter-method.md)|Obtém um ponteiro de interface para um `ICorDebugType` que faz referência ao primeiro <xref:System.Type> parâmetro genérico para o construtor da classe referenciada por isso `ICorDebugType` .|  
|[Método GetRank](icordebugtype-getrank-method.md)|Obtém o número de dimensões em um tipo de matriz.|  
|[Método GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md)|Obtém um ponteiro de interface para um ICorDebugValue que contém o valor do campo estático referenciado pelo token de campo especificado no quadro de ativação especificado.|  
|[Método GetType](icordebugtype-gettype-method.md)|Obtém um valor de CorElementType que descreve o tipo nativo do Common Language Runtime <xref:System.Type> referenciado por isso `ICorDebugType` .|  
  
## <a name="remarks"></a>Comentários  
 Se o tipo for genérico, `ICorDebugClass` representará o tipo não instanciado. A `ICorDebugType` interface representa um tipo genérico instanciado. Por exemplo, a tabela de hash \< K, V> seria representada por `ICorDebugClass` , enquanto a Hashtable \< Int32, a cadeia de caracteres> seria representada por `ICorDebugType` .  
  
 Tipos não genéricos são representados por `ICorDebugClass` e `ICorDebugType` . A última interface foi introduzida no .NET Framework versão 2,0 para lidar com a instanciação de tipo.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
