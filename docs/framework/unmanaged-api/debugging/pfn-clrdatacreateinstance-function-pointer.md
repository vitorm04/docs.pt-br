---
title: "Ponteiro de função PFN_CLRDataCreateInstance"
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
- PFN_CLRDataCreateInstance
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- PFN_CLRDataCreateInstance
helpviewer_keywords:
- PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 98a966434332549d9ceb7f29de81e19fa1b2108f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="pfnclrdatacreateinstance-function-pointer"></a>Ponteiro de função PFN_CLRDataCreateInstance
Aponta para uma função que cria um objeto de interface para o item de destino especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `iid`  
 [in] O identificador da interface a ser instanciado.  
  
 `target`  
 [in] Um ponteiro para um usuário implementado [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) objeto que representa o item de destino para o qual criar o objeto de interface.  
  
 `iface`  
 [out] Um ponteiro para o endereço do objeto retornado de interface.  
  
## <a name="remarks"></a>Comentários  
 O `ICLRDataTarget` objeto é implementado pelo gerador do aplicativo de depuração. A implementação depende do tipo de item de destino que está sendo representado. O item de destino pode ser um processo, despejo de memória, computador remoto e assim por diante.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando funções estáticas globais](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
