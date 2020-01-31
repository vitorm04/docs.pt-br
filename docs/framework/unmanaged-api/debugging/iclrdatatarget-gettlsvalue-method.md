---
title: Método ICLRDataTarget::GetTLSValue
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type:
- apiref
ms.openlocfilehash: d4e7c055480ea611357d5d3e18ac4306acf4d0b0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785413"
---
# <a name="iclrdatatargetgettlsvalue-method"></a>Método ICLRDataTarget::GetTLSValue
Obtém um valor do armazenamento local do thread (TLS) do thread especificado no processo de destino. Esse método é chamado pelos serviços de acesso a dados do Common Language Runtime (CLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `threadID`  
 no O identificador do sistema operacional de um thread no processo de destino.  
  
 `index`  
 no O índice do local. Esse valor deve ser um índice válido no repositório local do thread especificado.  
  
 `value`  
 fora Um ponteiro para um valor `CLRDATA_ADDRESS` que especifica o valor retornado do local TLS fornecido.  
  
## <a name="remarks"></a>Comentários  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData. idl, ClrData. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICLRDataTarget](iclrdatatarget-interface.md)
