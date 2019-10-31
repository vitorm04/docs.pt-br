---
title: Função GetMethod (referência de API não gerenciada)
description: A função GetMethod recupera informações sobre um método.
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 48986f5ff1cbbb45840ec1a059aa86711848d717
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102584"
---
# <a name="getmethod-function"></a>Função GetMethod

Recupera informações sobre o método especifico.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```

## <a name="parameters"></a>Parâmetros

`vFunc`\
no Este parâmetro não é usado.

`ptr`\
no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`\
no O nome do método. Esse parâmetro não pode ser `null` e deve apontar para um `LPCWSTR`válido.

`lFlags`\
[in] Reservado. Esse parâmetro deve ser 0.

`ppInSignature`\
fora Um ponteiro para o endereço de uma instância [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que descreve os parâmetros in para o método. Esse parâmetro será ignorado se for definido como `null`.

`ppOutSignature`\
fora Um ponteiro para o endereço de uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que descreve os parâmetros de saída para o método. Esse parâmetro será ignorado se for definido como `null`.

## <a name="return-value"></a>Valor retornado

Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | A propriedade especificada não foi encontrada. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IWbemClassObject:: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) .

O gerenciamento do Windows pode definir o ponteiro [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) para `null` se o método não tiver parâmetros in.

Em `ppInSignature` e `ppOutSignature` descrevem os parâmetros in e out, respectivamente, como propriedades em uma instância `IWbemClassObject` da classe System [_Parameters](/windows/desktop/WmiSdk/--parameters). As propriedades em `ppInSignature` são nomeadas `Param`*n*, em que *n* é a posição do parâmetro na assinatura do método (como `Param1`, `Param2`, etc.). As propriedades em `ppOutSignature` também são nomeadas `Param`*n*e o valor de retorno é nomeado `ReturnValue`. Para obter mais informações e um exemplo, consulte [método IWbemClassObject:: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

**Cabeçalho:** WMINet_Utils. idl

**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
