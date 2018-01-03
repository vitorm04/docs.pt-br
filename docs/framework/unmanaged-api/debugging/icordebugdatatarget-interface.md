---
title: Interface ICorDebugDataTarget
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget
helpviewer_keywords: ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5d3a3b190cfa606bd4239e24c5defdaff9f4257
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget-interface"></a>Interface ICorDebugDataTarget
Fornece uma interface de retorno de chamada que oferece acesso a um determinado processo de destino.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|Fornece informações sobre a plataforma, incluindo arquitetura de processador e sistema operacional, que está executando o processo de destino.|  
|[Método ReadVirtual](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|Obtém um bloco de memória contígua, iniciando no endereço especificado e o retorna no buffer fornecido.|  
|[Método GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|Solicita o contexto do thread atual para o segmento especificado.|  
  
## <a name="remarks"></a>Comentários  
 `ICorDebugDataTarget`e seus métodos têm as seguintes características:  
  
-   Os serviços de depuração chamar métodos nessa interface para acessar a memória e outros dados no processo de destino.  
  
-   O cliente do depurador deve implementar essa interface conforme apropriado para o destino específico (por exemplo, um processo em tempo real ou um despejo de memória).  
  
-   O `ICorDebugDataTarget` métodos podem ser chamados somente de dentro de métodos implementados em outros `ICorDebug*` interfaces. Isso garante que o cliente de depurador tem controle sobre qual thread é invocada e quando.  
  
-   O `ICorDebugDataTarget` implementação deve sempre retornar informações atualizadas sobre o destino.  
  
 O processo de destino deve ser interrompido e não alterado de alguma forma ao `ICorDebug*` interfaces (e, portanto, `ICorDebugDataTarget` métodos) está sendo chamado. Se o destino é um processo em tempo real e suas alterações de estado, o [Iclrdebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) método deve ser chamado novamente para fornecer uma instância de ICorDebugProcess de substituição.  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
