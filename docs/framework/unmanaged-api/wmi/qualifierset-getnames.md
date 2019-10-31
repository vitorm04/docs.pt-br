---
title: Função QualifierSet_GetNames (referência de API não gerenciada)
description: A função QualifierSet_GetNames recupera os nomes de qualificadores de um objeto ou propriedade.
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: bd0a67987dd8ffa825114726d066249aed40cf05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141698"
---
# <a name="qualifierset_getnames-function"></a>Função QualifierSet_GetNames

Recupera os nomes de todos os qualificadores ou de determinados qualificadores que estão disponíveis a partir do objeto ou da propriedade atual.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a>Parâmetros

`vFunc`\
no Este parâmetro não é usado.

`ptr`\
no Um ponteiro para uma instância de [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`lFlags`\
no Um dos seguintes sinalizadores ou valores que especifica quais nomes incluir na enumeração.

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|  | 0 | Retornar os nomes de todos os qualificadores. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Retornar somente os nomes de qualificadores específicos para a propriedade ou objeto atual. <br/> Para uma propriedade: retornar somente os qualificadores específicos à propriedade (incluindo substituições), e não os qualificadores propagados da definição de classe. <br/> Para uma instância: retornar apenas nomes de qualificador específicos da instância. <br/> Para uma classe: retornar somente qualificadores específicos à classe que está sendo derivada.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Retornar apenas os nomes dos qualificadores propagados de outro objeto. <br/> Para uma propriedade: retornar somente os qualificadores propagados para essa propriedade da definição de classe, e não os da própria propriedade. <br/> Para uma instância: retornar somente os qualificadores propagados da definição de classe. <br/> Para uma classe: retorna somente os nomes de qualificador herdados das classes pai. |

`pstrNames`\
fora Um novo `SAFEARRAY` que contém os nomes solicitados. A matriz pode ter 0 elementos. Se ocorrer um erro, um novo `SAFEARRAY` não será retornado.

## <a name="return-value"></a>Valor retornado

Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória suficiente disponível para iniciar uma nova enumeração. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IWbemQualifierSet:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) .

Depois de recuperar os nomes de qualificador, você pode acessar cada qualificador por nome chamando a função [QualifierSet_Get](qualifierset-get.md) .

Não é um erro para um determinado objeto ter nenhum qualificador, portanto, o número de cadeias de caracteres em `pstrNames` no retorno pode ser 0, mesmo que a função retorne `WBEM_S_NO_ERROR`.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

**Cabeçalho:** WMINet_Utils. idl

**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
