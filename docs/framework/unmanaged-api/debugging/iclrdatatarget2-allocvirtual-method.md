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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d9fc894cdd12e58689fb6b010820bb24d14a9541
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543741"
---
# <a name="iclrdatatarget2allocvirtual-method"></a>Método ICLRDataTarget2::AllocVirtual
Chamado pelo common language runtime (CLR) dados serviço de acesso para alocar memória no espaço de endereço desse processo de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `addr`  
 [in] Um `CLRDATA_ADDRESS` valor que especifica o endereço inicial solicitado da memória a ser alocado.  
  
 `size`  
 [in] O tamanho, em bytes, da memória a ser alocado.  
  
 `typeFlags`  
 [in] Sinalizadores que controlam a alocação de memória. Consulte o Win32 `VirtualAlloc` função.  
  
 `protectFlags`  
 [in] Os atributos de proteção para a memória alocada. Consulte o Win32 `VirtualAlloc` função.  
  
 `virt`  
 [out] Um ponteiro para um `CLRDATA_ADDRESS` valor que especifica o endereço inicial real da memória alocada.  
  
## <a name="remarks"></a>Comentários  
 O `AllocVirtual` método serve como um wrapper de lógico do Win32 `VirtualAlloc` função.  
  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [Método FreeVirtual](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
