---
title: Interface ICLRDataTarget2
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
ms.openlocfilehash: 6b2700b2f12e312f06640a06e5ec82fbc58f2ca9
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860467"
---
# <a name="iclrdatatarget2-interface"></a>Interface ICLRDataTarget2
Uma subclasse de [ICLRDataTarget](iclrdatatarget-interface.md) que é usada pela camada de serviços de acesso a dados para manipular regiões de memória virtual no processo de destino.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método AllocVirtual](iclrdatatarget2-allocvirtual-method.md)|Aloca memória no espaço de endereço do processo de destino.|  
|[Método FreeVirtual](iclrdatatarget2-freevirtual-method.md)|Libera a memória que foi alocada anteriormente no espaço de endereço do processo de destino.|  
  
## <a name="remarks"></a>Comentários  
 O cliente da API (ou seja, o depurador) deve implementar a interface conforme o apropriado para o processo de destino específico. Por exemplo, um processo dinâmico teria uma implementação diferente da implementação de um despejo de memória. O destino pode não oferecer suporte à modificação de suas regiões de memória.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData. idl, ClrData. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICLRDataTarget](iclrdatatarget-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
