---
title: Função QualifierSet_Put (referência de API não gerenciada)
description: A função QualifierSet_Put grava o qualificador nomeado e seu valor.
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: a35025c6d16455a51b7b22d822ba77337ddd894a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120229"
---
# <a name="qualifierset_put-function"></a>Função QualifierSet_Put

Grava o qualificador nomeado e o valor. O novo qualificador substitui o valor anterior do mesmo nome. Se o qualificador não existir, ele será criado.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT QualifierSet_Put (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
);
```

## <a name="parameters"></a>Parâmetros

`vFunc`\
no Este parâmetro não é usado.

`ptr`\
no Um ponteiro para uma instância de [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`wszName`\
no O nome do qualificador a ser gravado.

`pVal`\
no Um ponteiro para um `VARIANT` válido que contém o qualificador para gravação. O parâmetro não pode ser `null`.

`lFlavor`\
no Uma das constantes a seguir que define os tipos de qualificador desejado para este qualificador. O valor padrão é `WBEM_FLAVOR_OVERRIDABLE` (0).

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | O qualificador pode ser substituído em uma classe ou instância derivada. **Esse é o valor padrão.** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1 | O qualificador é propagado para instâncias. |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | O qualificador é propagado para classes derivadas. |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | 0x10 | O qualificador não pode ser substituído em uma instância ou classe derivada. |
| `WBEM_FLAVOR_AMENDED` | 0x80 | O qualificador está localizado. |

## <a name="return-value"></a>Valor retornado

Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | Houve uma tentativa inválida de especificar o qualificador de **chave** em uma propriedade que não pode ser uma chave. As chaves são especificadas na definição de classe para um objeto e não podem ser alteradas por instância. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | O parâmetro `pVal` não é de um tipo de qualificador legal. |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | Não é possível chamar o método `QualifierSet_Put` no qualificador porque o objeto proprietário não permite substituições. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IWbemQualifierSet::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) .

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

**Cabeçalho:** WMINet_Utils. idl

**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
