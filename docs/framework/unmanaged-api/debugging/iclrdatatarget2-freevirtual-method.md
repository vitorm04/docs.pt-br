---
title: Método ICLRDataTarget2::FreeVirtual
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
ms.openlocfilehash: 7eda9bfff6de6b386c16ad0a188931d9d3adcb93
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793667"
---
# <a name="iclrdatatarget2freevirtual-method"></a>Método ICLRDataTarget2::FreeVirtual
Chamado pelos serviços de acesso a dados do Common Language Runtime (CLR) para liberar memória que foi alocada anteriormente no espaço de endereço do processo de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `addr`  
 no Um valor `CLRDATA_ADDRESS` que especifica o endereço inicial da memória a ser liberada.  
  
 `size`  
 no O tamanho, em bytes, da memória a ser liberada.  
  
 `typeFlags`  
 no Sinalizadores que controlam a liberação de memória. Consulte a função de `VirtualFree` do Win32.  
  
## <a name="remarks"></a>Comentários  
 O método `FreeVirtual` serve como um wrapper lógico para a função de `VirtualFree` do Win32.  
  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData. idl, ClrData. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICLRDataTarget2](iclrdatatarget2-interface.md)
- [Método AllocVirtual](iclrdatatarget2-allocvirtual-method.md)
