---
title: Função CompareTo (referência de API não gerenciada)
description: A função CompareTo compara um objeto com outro objeto WMI.
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0d210795016cd2e0179b902a224ca0c62f4ac01f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128706"
---
# <a name="compareto-function"></a>Função CompareTo

Compara um objeto a outro objeto de gerenciamento do Windows.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CompareTo (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo
);
```

## <a name="parameters"></a>Parâmetros

`vFunc`\
no Este parâmetro não é usado.

`ptr`\
no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`flags`\
no Uma combinação de bits de bit que especifica as características do objeto a serem consideradas para a comparação. Consulte a seção [comentários](#remarks) para obter mais informações.

`pCompareTo`\
no O objeto para comparação. `pCompareTo` deve ser uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) válida; Não pode ser `null`.

## <a name="return-value"></a>Valor retornado

Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Ocorreu um erro não especificado. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro é inválido. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Uma segunda chamada para `BeginEnumeration` foi feita sem uma chamada intermediária para [`EndEnumeration`](endenumeration.md). |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
| `WBEM_S_DIFFERENT` | 0x40003 | Os objetos são diferentes. |
| `WBEM_S_SAME` | 0 | Os objetos são os mesmos com base nos sinalizadores de comparação. |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IWbemClassObject:: CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) .

Os sinalizadores que podem ser passados como o argumento `lEnumFlags` são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código. Você pode especificar as características individuais envolvidas na comparação, especificando uma combinação bit a bit dos seguintes sinalizadores:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | Ignorar a origem (o servidor e o namespace do qual vieram). |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1 | Ignorar todos os qualificadores (incluindo **chave** e **dinâmica**) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | Ignorar valores padrão de propriedades. Esse sinalizador se aplica somente à comparação de classes. |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | Ignore os tipos de qualificador. Esse sinalizador ainda usa qualificadores em conta, mas ignora as distinções de flavor, como regras de propagação e restrições de substituição. |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | Ignorar maiúsculas na comparação de valores de cadeia de caracteres. Isso se aplica tanto a cadeias de caracteres quanto a valores de qualificador. A comparação dos nomes de propriedade e qualificador sempre diferencia maiúsculas de minúsculas, independentemente de o sinalizador ser definido ou não. |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | Suponha que os objetos que estão sendo comparados sejam instâncias da mesma classe. Consequentemente, esse sinalizador compara apenas informações relacionadas à instância. Use esses sinalizadores para otimizar o desempenho. Se os objetos não são da mesma classe, os resultados são indefinidos. |

Ou você pode especificar um único sinalizador composto da seguinte maneira:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | Considere todos os recursos na comparação. |

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

**Cabeçalho:** WMINet_Utils. idl

**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
