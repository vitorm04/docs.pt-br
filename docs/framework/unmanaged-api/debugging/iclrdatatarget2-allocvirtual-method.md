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
ms.openlocfilehash: 46532592057f4fa6d9883d46dcef2f8f9e5f7228
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406338"
---
# <a name="iclrdatatarget2allocvirtual-method"></a>Método ICLRDataTarget2::AllocVirtual
Chamado pelos comuns language runtime (CLR) dados serviços de acesso para alocar memória no espaço de endereço desse processo de destino.  
  
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
 [in] Um `CLRDATA_ADDRESS` valor que especifica o endereço inicial solicitado de memória a ser alocada.  
  
 `size`  
 [in] O tamanho, em bytes, da memória a ser alocada.  
  
 `typeFlags`  
 [in] Sinalizadores que controlam a alocação de memória. Consulte o Win32 `VirtualAlloc` função.  
  
 `protectFlags`  
 [in] Os atributos de proteção para a memória alocada. Consulte o Win32 `VirtualAlloc` função.  
  
 `virt`  
 [out] Um ponteiro para um `CLRDATA_ADDRESS` valor que especifica o endereço inicial real da memória alocada.  
  
## <a name="remarks"></a>Comentários  
 O `AllocVirtual` método serve como um wrapper lógico para o Win32 `VirtualAlloc` função.  
  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [Método FreeVirtual](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
