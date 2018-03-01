---
title: Interface ICorDebugAppDomain3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 017a2f018569b17c0b0011638e16f1921b6c9801
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain3-interface"></a>Interface ICorDebugAppDomain3
Fornece métodos para recuperar informações sobre as representações gerenciadas de [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos atualmente carregados em um domínio de aplicativo. Essa interface é uma extensão das interfaces ICorDebugAppDomain e ICorDebugAppDomain2.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Icordebugappdomain3](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|Obtém um enumerador para todos armazenados em cache [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos.|  
|[Icordebugappdomain3](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|Obtém um enumerador para armazenada em cache [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos em um domínio de aplicativo com base em seus identificadores de interface.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface destina-se a ser usado por um depurador em conjunto com uma chamada de função de avaliação para `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`. Quando o método recupera os identificadores de interface com suporte por um [!INCLUDE[wrt](../../../../includes/wrt-md.md)] objeto de servidor, o depurador pode usar os métodos definidos nessa interface mapeá-los para os tipos gerenciados que correspondem a essas interfaces.  
  
 Para recuperar uma instância desta interface, executar `QueryInterface` em uma instância da interface ICorDebugAppDomain ou ICorDebugAppDomain2.  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
