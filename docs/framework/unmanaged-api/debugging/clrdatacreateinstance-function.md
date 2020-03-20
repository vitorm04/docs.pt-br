---
title: Função CLRDataCreateInstance
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- COM
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
ms.openlocfilehash: c24963a6e56adfb9f763c6521027744db82cc357
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179356"
---
# <a name="clrdatacreateinstance-function"></a>Função CLRDataCreateInstance
Cria um objeto de interface para o item de destino especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,
    [in]  ICLRDataTarget  *target,
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `iid`  
 [em] O identificador da interface a ser instanciado.  
  
 `target`  
 [em] Um ponteiro para um objeto [ICLRDataTarget](iclrdatatarget-interface.md) implementado pelo usuário que representa o item de destino para o qual criar o objeto de interface.  
  
 `iface`  
 [fora] Um ponteiro para o endereço do objeto de interface retornado.  
  
## <a name="remarks"></a>Comentários  
 O `ICLRDataTarget` objeto é implementado pelo autor do aplicativo de depuração. A implementação depende do tipo de item-alvo que está sendo representado. O item de destino pode ser um processo, despejo de memória, máquina remota, e assim por diante.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Depurando funções estáticas globais](debugging-global-static-functions.md)
