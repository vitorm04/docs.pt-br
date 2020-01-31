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
ms.openlocfilehash: 8210e67f4bdd615ff65d9bd3474043fc45fd8883
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791254"
---
# <a name="icordebugtype-interface"></a>Interface ICorDebugType
Representa um tipo, básico ou complexo (ou seja, definido pelo usuário). Se o tipo for genérico, `ICorDebugType` representará o tipo genérico instanciado.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumerateTypeParameters](icordebugtype-enumeratetypeparameters-method.md)|Obtém um ponteiro de interface para um ICorDebugTypeEnum que faz referência aos parâmetros de <xref:System.Type> genéricos da classe referenciada por este `ICorDebugType`.|  
|[Método GetBase](icordebugtype-getbase-method.md)|Obtém um ponteiro de interface para um `ICorDebugType` que faz referência à classe base da classe referenciada por essa `ICorDebugType`, se existir uma.|  
|[Método GetClass](icordebugtype-getclass-method.md)|Obtém um ponteiro de interface para um ICorDebugClass que faz referência ao Construtor tipado dessa `ICorDebugType`.|  
|[Método GetFirstTypeParameter](icordebugtype-getfirsttypeparameter-method.md)|Obtém um ponteiro de interface para um `ICorDebugType` que faz referência ao primeiro parâmetro de <xref:System.Type> genérico para o construtor da classe referenciada por essa `ICorDebugType`.|  
|[Método GetRank](icordebugtype-getrank-method.md)|Obtém o número de dimensões em um tipo de matriz.|  
|[Método GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md)|Obtém um ponteiro de interface para um ICorDebugValue que contém o valor do campo estático referenciado pelo token de campo especificado no quadro de ativação especificado.|  
|[Método GetType](icordebugtype-gettype-method.md)|Obtém um valor de CorElementType que descreve o tipo nativo do Common Language Runtime <xref:System.Type> referenciado por esse `ICorDebugType`.|  
  
## <a name="remarks"></a>Comentários  
 Se o tipo for genérico, `ICorDebugClass` representará o tipo não instanciado. A interface `ICorDebugType` representa um tipo genérico instanciado. Por exemplo, a tabela de hash\<K, V > seria representada por `ICorDebugClass`, enquanto a Hashtable\<Int32, a cadeia de caracteres > seria representada por `ICorDebugType`.  
  
 Tipos não genéricos são representados por `ICorDebugClass` e `ICorDebugType`. A última interface foi introduzida no .NET Framework versão 2,0 para lidar com a instanciação de tipo.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
