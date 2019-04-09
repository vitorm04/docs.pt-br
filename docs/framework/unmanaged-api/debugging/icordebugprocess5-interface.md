---
title: Interface ICorDebugProcess5
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5904083be66d4bd6dc69729bebc28db8a800e77
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089220"
---
# <a name="icordebugprocess5-interface"></a>Interface ICorDebugProcess5
Estende a interface ICorDebugProcess para suportar o acesso para o heap gerenciado, para fornecer informações sobre a coleta de lixo de objetos gerenciados, e determinar se um depurador carrega imagens do cache de imagem nativo local do aplicativo.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnableNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|Define um valor que determina como um aplicativo carrega as imagens nativas durante a execução em um depurador gerenciado.|  
|[Método EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|Obtém um enumerador para todos os objetos que precisam estar em um processo de coleta de lixo.|  
|[Método EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|Obtém um enumerador para os identificadores de objeto em um processo.|  
|[Método EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|Obtém um enumerador para objetos no heap gerenciado.|  
|[Método EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|Obtém um enumerador para regiões do heap gerenciado.|  
|[Método GetArrayLayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|Obtém informações sobre o layout de uma matriz na memória.|  
|[Método GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|Obtém um ponteiro para um [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) estrutura que contém informações sobre os objetos que devem ser coletado como lixo no heap gerenciado.|  
|[Método GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|Obtém um ponteiro para um objeto no heap gerenciado.|  
|[Método GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|Obtém um ponteiro para uma matriz que contém informações de campo para um tipo com base em seu identificador de tipo.|  
|[Método GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|Obtém um objeto do tipo que fornece informações sobre um objeto com base em seus identificadores de tipo.|  
|[Método GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|Obtém o identificador de tipo para o objeto em um endereço especificado.|  
|[Método GetTypeLayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|Obtém informações sobre o layout de um objeto na memória com base em seu identificador de tipo.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface estende logicamente a ICorDebugProcess, ICorDebugProcess2, e [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfaces.  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, de outro computador ou de outro processo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
