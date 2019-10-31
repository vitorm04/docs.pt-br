---
title: Função FormatFromRawValue (referência de API não gerenciada)
description: A função FormatFromRawValue converte dados brutos de desempenho em um formato especificado.
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5097cfe43ae785461a1e2af1217bcbd5e8c4b79c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120282"
---
# <a name="formatfromrawvalue-function"></a>Função FormatFromRawValue
Converte um valor de dados de desempenho brutos para o formato especificado, ou dois valores de dados de desempenho brutos se a conversão de formato é baseada em tempo. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```

## <a name="parameters"></a>Parâmetros

`dwCounterType`\
no O tipo de contador. Para obter uma lista de tipos de contadores, consulte [tipos de contador de desempenho WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types). `dwCounterType` pode ser qualquer tipo de contador, exceto `PERF_LARGE_RAW_FRACTION` e `PERF_LARGE_RAW_BASE`. 

`dwFormat`\
no O formato para o qual converter os dados de desempenho brutos. Pode ser um dos seguintes valores:

|Constante  |Valor  |Descrição |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Retorna o valor calculado como um valor de ponto flutuante de precisão dupla. | 
| `PDH_FMT_LARGE` | 0x00000400 | Retorne o valor calculado como um inteiro de 64 bits. |
| `PDH_FMT_LONG` | 0x00000100 | Retorne o valor calculado como um inteiro de 32 bits. |

Um dos valores anteriores pode ser vinculada com um dos seguintes sinalizadores de dimensionamento:

|Constante  |Valor  |Descrição |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | Não aplique os fatores de dimensionamento do contador. |
| `PDH_FMT_1000` | 0x00002000 | Multiplique o valor final por 1.000. | 

`pTimeBase`\
no Um ponteiro para a base de tempo, se necessário para a conversão de formato. Se as informações de base de tempo não forem necessárias para a conversão de formato, o valor desse parâmetro será ignorado.

`pRawValue1`\ [in] um ponteiro para uma estrutura de [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) que representa um valor de desempenho bruto.

`pRawValue2`\
no Um ponteiro para uma estrutura de [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) que representa um segundo valor de desempenho bruto. Se um segundo valor de desempenho bruto não for necessário, esse parâmetro deverá ser `null`.

`pFmtValue`\
fora Um ponteiro para uma estrutura de [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) que recebe o valor de desempenho formatado.

## <a name="return-value"></a>Valor retornado

Os valores a seguir são retornados por essa função:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | A chamada de função foi bem-sucedida. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Um argumento necessário está ausente ou incorreto. | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | O identificador não é um objeto PDH válido. |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para a função [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) .

## <a name="requirements"></a>Requisitos

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

 **Biblioteca:** PerfCounter. dll

 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
