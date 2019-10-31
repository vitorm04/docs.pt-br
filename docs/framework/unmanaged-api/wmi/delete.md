---
title: Função Delete (referência de API não gerenciada)
description: A função Delete exclui a propriedade especificada e todos os seus qualificadores de uma definição de classe CIM.
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6b8f287be831702dd31a8335f9b2f6447bcee540
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127658"
---
# <a name="delete-function"></a>Função Delete

Exclui a propriedade especificada e todos os seus qualificadores de uma definição de classe CIM.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```

## <a name="parameters"></a>Parâmetros

`vFunc`\
no Este parâmetro não é usado.

`ptr`\
no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`\
no O nome da propriedade a ser excluída. `wszName` deve ser um ponteiro para um `LPCWSTR`válido.

## <a name="return-value"></a>Valor retornado

Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Ocorreu um erro não especificado. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | A propriedade não pode ser excluída. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName` é inválido. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | A propriedade especificada não existe. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória suficiente para concluir a operação. |
| `WBEM_E_PROPAGATED_PROPERTY` | 0x8004101c | A propriedade é herdada de uma classe base. |
| `WBEM_E_SYSTEM_PROPERTY` | | A propriedade é uma propriedade do sistema. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
| `WBEM_E_RESET_TO_DEFAULT` | 0x80041030 | A função excluiu um valor padrão de substituição para a classe atual. O valor padrão para essa propriedade na classe pai foi reativado. |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IWbemClassObject::D xcluir](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) .

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

**Cabeçalho:** WMINet_Utils. idl

**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
