---
title: Função FormatFromRawValue (referência de API não gerenciada)
description: A função FormatFromRawValue converte dados de desempenho bruto em um formato especificado.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 420a02d2f7757c52d6e8ff92a9ca30e44938cd18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546433"
---
# <a name="formatfromrawvalue-function"></a>Função FormatFromRawValue
Converte um valor de dados de desempenho brutos para o formato especificado, ou dois valores de dados de desempenho brutos se a conversão de formato é baseada em tempo.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
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

`dwCounterType`  
[in] O tipo de contador. Para obter uma lista dos tipos de contador, consulte [tipos de contador de desempenho WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types). `dwCounterType` pode ser qualquer tipo de contador, exceto `PERF_LARGE_RAW_FRACTION` e `PERF_LARGE_RAW_BASE`. 

`dwFormat`  
[in] O formato para o qual converter os dados de desempenho bruto. Ele pode ser um dos seguintes valores:

|Constante  |Valor  |Descrição |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Retorna o valor calculado como um valor de ponto flutuante de precisão dupla. | 
| `PDH_FMT_LARGE` | 0x00000400 | Retorna o valor calculado como um inteiro de 64 bits. |
| `PDH_FMT_LONG` | 0x00000100 | Retorna o valor calculado como um inteiro de 32 bits. |

Um dos valores anteriores pode estar ORed com um dos seguintes sinalizadores de colocação em escala:

|Constante  |Valor  |Descrição |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | Não se aplicam os fatores de dimensionamento do contador. |
| `PDH_FMT_1000` | 0x00002000 | Multiplique o valor final por 1.000. | 

`pTimeBase`  
[in] Um ponteiro para a base de tempo, se necessário para a conversão de formato. Se as informações de base de tempo não são necessárias para a conversão de formato, o valor desse parâmetro é ignorado.

`pRawValue1` [in] Um ponteiro para um [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) estrutura que representa um valor de desempenho bruto.

`pRawValue2` [in] Um ponteiro para um [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) estrutura que representa um segundo valor de desempenho bruto. Se um segundo valor de desempenho bruto não é necessário, esse parâmetro deve ser `null`.

`pFmtValue` [out] Um ponteiro para um [ `PDH_FMT_COUNTERVALUE` ](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue) estrutura que recebe o valor formatado de desempenho.

## <a name="return-value"></a>Valor retornado

Os seguintes valores são retornados por essa função:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | A chamada de função for bem-sucedida. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Um argumento necessário está ausente ou incorreto. | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | O identificador não é um objeto PDH válido. |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [FormatFromRawValue](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms231047%28v=vs.85%29) função.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Biblioteca:** PerfCounter.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também
- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
