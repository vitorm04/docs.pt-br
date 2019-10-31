---
title: Função QualifierSet_BeginEnumeration (referência de API não gerenciada)
description: A função QualifierSet_BeginEnumeration redefine um enumerador dos qualificadores de um objeto.
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 79edbd876fc9992f088b9adb159e005c735a72cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127319"
---
# <a name="qualifierset_beginenumeration-function"></a>Função QualifierSet_BeginEnumeration

Redefine um enumerador dos qualificadores de um objeto para o início da enumeração.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a>Parâmetros

`vFunc`\
no Este parâmetro não é usado.

`ptr`\
no Um ponteiro para uma instância de [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`lFlags`\
no Uma combinação de bits de bit que indica os sinalizadores ou valores descritos na seção [comentários](#remarks) que especifica os qualificadores a serem incluídos na enumeração.

## <a name="return-value"></a>Valor retornado

Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | O parâmetro `lFlags` não é válido. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Uma segunda chamada para `QualifierSet_BeginEnumeration` foi feita sem uma chamada intermediária para [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória suficiente disponível para iniciar uma nova enumeração. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IWbemQualifierSet:: BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) .

Para enumerar todos os qualificadores em um objeto, esse método deve ser chamado antes da primeira chamada para [QualifierSet_Next](qualifierset-next.md). A ordem na qual os qualificadores são enumerados é garantida para ser invariável para uma determinada enumeração.

Os sinalizadores que podem ser passados como o argumento `lEnumFlags` são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código.

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|  | 0 | Retornar os nomes de todos os qualificadores. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Retornar somente os nomes de qualificadores específicos para a propriedade ou objeto atual. <br/> Para uma propriedade: retornar somente os qualificadores específicos à propriedade (incluindo substituições), e não os qualificadores propagados da definição de classe. <br/> Para uma instância: retornar apenas nomes de qualificador específicos da instância. <br/> Para uma classe: retornar somente qualificadores específicos à classe que está sendo derivada.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Retornar apenas os nomes dos qualificadores propagados de outro objeto. <br/> Para uma propriedade: retornar somente os qualificadores propagados para essa propriedade da definição de classe, e não os da própria propriedade. <br/> Para uma instância: retornar somente os qualificadores propagados da definição de classe. <br/> Para uma classe: retorna somente os nomes de qualificador herdados das classes pai. |

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

**Cabeçalho:** WMINet_Utils. idl

**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
