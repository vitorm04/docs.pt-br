---
title: Função FormatFromRawValue (referência de API não gerenciada)
description: A função FormatFromRawValue converte dados de desempenho bruto sumidos para um formato especificado.
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
ms.openlocfilehash: 0a7c0b8387f0c8e2b6e2ade94f7efeede75bd758
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176832"
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

## <a name="parameters"></a>parâmetros

`dwCounterType`\
[em] O tipo de contador. Para obter uma lista de tipos de contador, consulte [Tipos de contador de desempenho WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types). `dwCounterType`pode ser qualquer tipo `PERF_LARGE_RAW_FRACTION` `PERF_LARGE_RAW_BASE`de contador, exceto e .

`dwFormat`\
[em] O formato para converter os dados de desempenho bruto. Pode ser um dos seguintes valores:

|Constante  |Valor  |Descrição |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Devolva o valor calculado como um valor de ponto flutuante de dupla precisão. |
| `PDH_FMT_LARGE` | 0x00000400 | Devolva o valor calculado como um inteiro de 64 bits. |
| `PDH_FMT_LONG` | 0x00000100 | Devolva o valor calculado como um inteiro de 32 bits. |

Um dos valores anteriores pode ser ORed com uma das seguintes bandeiras de escala:

|Constante  |Valor  |Descrição |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | Não aplique os fatores de dimensionamento do contador. |
| `PDH_FMT_1000` | 0x00002000 | Multiplique o valor final por 1.000. |

`pTimeBase`\
[em] Um ponteiro para a base de tempo, se necessário para a conversão de formato. Se as informações da base de tempo não forem necessárias para a conversão do formato, o valor deste parâmetro será ignorado.

`pRawValue1`\
[em] Um ponteiro [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) para uma estrutura que representa um valor bruto de desempenho.

`pRawValue2`\
[em] Um ponteiro [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) para uma estrutura que representa um segundo valor bruto de desempenho. Se um segundo valor de desempenho bruto não `null`for necessário, este parâmetro deve ser .

`pFmtValue`\
[fora] Um ponteiro [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) para uma estrutura que recebe o valor de desempenho formatado.

## <a name="return-value"></a>Valor retornado

Os seguintes valores são retornados por esta função:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | A chamada de função é bem sucedida. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Um argumento necessário está faltando ou incorreto. |
| `PDH_INVALID_HANDLE` | 0xC0000BBC | A alça não é um objeto PDH válido. |

## <a name="remarks"></a>Comentários

Esta função envolve uma chamada para a função [FormatFromRawValue.](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85))

## <a name="requirements"></a>Requisitos

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

 **Biblioteca:** PerfCounter.dll

 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
