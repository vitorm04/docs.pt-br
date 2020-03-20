---
title: Função GetDemultiplexedStub (referência de API não gerenciada)
description: A função GetDemultiplexedStub cria um dissipador de reencaminhador de objetos para ajudar um cliente a receber chamadas assíncronas do Gerenciamento do Windows.
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: d15fed261db2ca2cda6dbf824dc9cb0d5c56eed3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174960"
---
# <a name="getdemultiplexedstub-function"></a>Função GetDemultiplexedStub
Cria um coletor do encaminhador de objeto para ajudar um cliente a receber chamadas assíncronas do Gerenciamento do Windows.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject,
   [in] boolean      isLocal,
   [out] IUnknown**  ppObject
);
```  

## <a name="parameters"></a>parâmetros

`pObject`  
[em] Um ponteiro para a implementação em processo do [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink)do cliente .

`isLocal`  
[em] Uma bandeira que indica se`true`o evento é local ( ); caso contrário, `false`.

`ppObject`  
[fora] Um sistema de encaminhamento de objetos afunda para ajudar um cliente a receber chamadas assíncronas do Gerenciamento do Windows.

## <a name="return-value"></a>Valor retornado

Se a função for bem `S_OK` sucedida, o valor de retorno será (0).

Se a função falhar, o valor de retorno será um código de erro não-zero. Para obter informações de erro estendidas, ligue para a função [GetErrorInfo.](geterrorinfo.md)

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
