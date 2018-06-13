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
ms.openlocfilehash: e0710b26237b350f1dfbc7d2464b7a131373604e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460415"
---
# <a name="formatfromrawvalue-function"></a>Função FormatFromRawValue
Converte um valor de dados de desempenho bruto para o formato especificado ou dois valores de dados de desempenho bruto se a conversão de formato é baseado no tempo.   
  
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
[in] O tipo de contador. Para obter uma lista dos tipos de contador, consulte [tipos de contador de desempenho WMI](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx). `dwCounterType` pode ser qualquer tipo de contador, exceto para `PERF_LARGE_RAW_FRACTION` e `PERF_LARGE_RAW_BASE`. 

`dwFormat`  
[in] O formato no qual converter os dados de desempenho bruto. Pode ser um dos seguintes valores:

|Constante  |Valor  |Descrição |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Retorna o valor calculado como um valor de ponto flutuante de precisão dupla. | 
| `PDH_FMT_LARGE` | 0x00000400 | Retorna o valor calculado como um inteiro de 64 bits. |
| `PDH_FMT_LONG` | 0x00000100 | Retorna o valor calculado como um inteiro de 32 bits. |

Um dos valores anteriores pode ser ORed com um dos seguintes sinalizadores de dimensionamento:

|Constante  |Valor  |Descrição |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | Não aplique os fatores de dimensionamento do contador. |
| `PDH_FMT_1000` | 0x00002000 | Multiplica o valor final por 1.000. | 

`pTimeBase`  
[in] Um ponteiro para a base de tempo para a conversão de formato, se necessário. Se as informações de base de tempo não são necessárias para a conversão de formato, o valor desse parâmetro é ignorado.

`pRawValue1` [in] Um ponteiro para um [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) estrutura que representa um valor de desempenho bruto.

`pRawValue2` [in] Um ponteiro para um [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) estrutura que representa um segundo valor de desempenho bruto. Se um segundo valor de desempenho bruto não é necessário, esse parâmetro deve ser `null`.

`pFmtValue` [out] Um ponteiro para um [ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) estrutura que recebe o valor formatado de desempenho.

## <a name="return-value"></a>Valor retornado

Os seguintes valores são retornados por essa função:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | A chamada de função foi bem-sucedida. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Um argumento necessário está ausente ou incorreto. | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | O identificador não é um objeto PDH válido. |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) função.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Biblioteca:** PerfCounter.dll  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
