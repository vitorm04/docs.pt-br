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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b30bd3e97af8d222f629c5b4f9f318a9b6379e78
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181396"
---
# <a name="iclrdatatarget2freevirtual-method"></a>Método ICLRDataTarget2::FreeVirtual
Chamado pelo serviço common language runtime (CLR) data access para liberar memória que foi alocado anteriormente no espaço de endereço do processo de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `addr`  
 [in] Um `CLRDATA_ADDRESS` valor que especifica o endereço inicial da memória a ser liberado.  
  
 `size`  
 [in] O tamanho, em bytes, da memória a ser liberado.  
  
 `typeFlags`  
 [in] Sinalizadores que controlam a liberação de memória. Consulte o Win32 `VirtualFree` função.  
  
## <a name="remarks"></a>Comentários  
 O `FreeVirtual` método serve como um wrapper de lógico do Win32 `VirtualFree` função.  
  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [Método AllocVirtual](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
