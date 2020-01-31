---
title: Método ICLRDataTarget2::AllocVirtual
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.AllocVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type:
- apiref
ms.openlocfilehash: 51c06a7f8ea22fc73236131954781d8755274041
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789081"
---
# <a name="iclrdatatarget2allocvirtual-method"></a>Método ICLRDataTarget2::AllocVirtual
Chamado pelos serviços de acesso a dados do Common Language Runtime (CLR) para alocar memória no espaço de endereço desse processo de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `addr`  
 no Um valor `CLRDATA_ADDRESS` que especifica o endereço inicial solicitado da memória a ser alocada.  
  
 `size`  
 no O tamanho, em bytes, da memória a ser alocada.  
  
 `typeFlags`  
 no Sinalizadores que controlam a alocação de memória. Consulte a função de `VirtualAlloc` do Win32.  
  
 `protectFlags`  
 no Os atributos de proteção para a memória alocada. Consulte a função de `VirtualAlloc` do Win32.  
  
 `virt`  
 fora Um ponteiro para um valor `CLRDATA_ADDRESS` que especifica o endereço inicial real da memória alocada.  
  
## <a name="remarks"></a>Comentários  
 O método `AllocVirtual` serve como um wrapper lógico para a função de `VirtualAlloc` do Win32.  
  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData. idl, ClrData. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICLRDataTarget2](iclrdatatarget2-interface.md)
- [Método FreeVirtual](iclrdatatarget2-freevirtual-method.md)
