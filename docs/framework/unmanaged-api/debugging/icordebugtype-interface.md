---
title: ICorDebugType Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de2871b406bb9da84d20d7c526ad4a703baae409
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugtype-interface1"></a>ICorDebugType Interface1
Representa um tipo básico ou complexo (que é, definido pelo usuário). Se o tipo for genérico, `ICorDebugType` representará o tipo genérico instanciado.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|Obtém um ponteiro de interface para um ICorDebugTypeEnum que faz referência genérica <xref:System.Type> parâmetros da classe referenciada por este `ICorDebugType`.|  
|[Método GetBase](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|Obtém um ponteiro de interface para um `ICorDebugType` que referencia a classe base da classe referenciada por este `ICorDebugType`, se houver.|  
|[Método GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|Obtém um ponteiro de interface para um ICorDebugClass que referencia o construtor com tipo deste `ICorDebugType`.|  
|[Método GetFirstTypeParameter](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|Obtém um ponteiro de interface para um `ICorDebugType` que referencia o primeiro genérico <xref:System.Type> parâmetro para o construtor da classe referenciada por este `ICorDebugType`.|  
|[Método GetRank](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|Obtém o número de dimensões em um tipo de matriz.|  
|[Método GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|Obtém um ponteiro de interface para um ICorDebugValue que contém o valor do campo estático referenciado pelo campo especificado token no quadro de pilha especificada.|  
|[Método GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|Obtém um valor de CorElementType que descreve o tipo nativo do common language runtime <xref:System.Type> referenciada por este `ICorDebugType`.|  
  
## <a name="remarks"></a>Comentários  
 Se o tipo for genérico, `ICorDebugClass` representa o tipo instanciado. O `ICorDebugType` interface representa um tipo genérico instanciado. Por exemplo, tabela de hash\<K, V > seria representado por `ICorDebugClass`, enquanto Hashtable\<Int32, a cadeia de caracteres > seria representado por `ICorDebugType`.  
  
 Tipos genéricos não são representados por ambos `ICorDebugClass` e `ICorDebugType`. A segunda interface foi introduzida no .NET Framework versão 2.0 para lidar com uma instância de tipo.  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
