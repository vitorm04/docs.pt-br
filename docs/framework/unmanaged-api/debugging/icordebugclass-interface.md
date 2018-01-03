---
title: ICorDebugClass Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass
helpviewer_keywords: ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3998cf76430612759f69df07fb4f5afebd7a25ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugclass-interface1"></a>ICorDebugClass Interface1
Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário). Se o tipo for genérico, `ICorDebugClass` representará o tipo genérico sem instância.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Obtém o módulo que define essa classe.|  
|[Método GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|Obtém o valor do campo estático especificado.|  
|[Método GetToken](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|Obtém o `TypeDef` token de metadados para essa classe.|  
  
## <a name="remarks"></a>Comentários  
 O `ICorDebugClass` interface representa um tipo genérico instanciado. A interface ICorDebugType representa um tipo genérico instanciado. Por exemplo, `Hashtable<K, V>` poderia ser representado por `ICorDebugClass`, enquanto `Hashtable<Int32, String>` poderia ser representado por `ICorDebugType`.  
  
 Tipos genéricos não são representados por ambos `ICorDebugClass` e `ICorDebugType`. A segunda interface foi introduzida no .NET Framework versão 2.0 para lidar com uma instância de tipo.  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
