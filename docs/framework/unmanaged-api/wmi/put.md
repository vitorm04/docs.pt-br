---
title: Função put (referência de API não gerenciada)
description: A função Put atribui um novo valor a uma propriedade nomeada.
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5aa629c2d07fb25db035cd80aba3c74413070e6e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798403"
---
# <a name="put-function"></a>Função put

Define uma propriedade nomeada para um novo valor.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Put (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
);
```

## <a name="parameters"></a>Parâmetros

`vFunc`\
no Este parâmetro não é usado.

`ptr`\
no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`\
no O nome da propriedade. O parâmetro não pode ser `null`.

`lFlags`\
[in] Reservado. Esse parâmetro deve ser 0.

`pVal`\
no Um ponteiro para um válido `VARIANT` que se torna o novo valor da propriedade. Se `pVal` `VARIANT` for `null` ou apontar para um de tipo `VT_NULL`, a propriedade será definida como `null`.

`vtType`\
no O tipo de `VARIANT` apontado por `pVal`. Consulte a seção [comentários](#remarks) para obter mais informações.

## <a name="return-value"></a>Valor retornado

Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Houve uma falha geral. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um ou mais parâmetros não são válidos. |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | O tipo de propriedade não é reconhecido. Esse valor é retornado ao criar instâncias de classe se a classe já existir. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | Para instâncias: Indica que `pVal` aponta para um `VARIANT` tipo incorreto para a propriedade. <br/> Para definições de classe: A propriedade já existe na classe pai e o novo tipo COM é diferente do tipo COM antigo. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida. |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IWbemClassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .

Essa função sempre substitui o valor da propriedade atual por um novo. Se o [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) apontar para uma definição de classe `Put` , criará ou atualizará o valor da propriedade. Quando [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) aponta para uma instância CIM, `Put` o atualiza somente o valor da propriedade; `Put` não é possível criar um valor de propriedade.

A `__CLASS` Propriedade do sistema só é gravável durante a criação da classe, quando não pode ser deixada em branco. Todas as outras propriedades do sistema são somente leitura.

Um usuário não pode criar propriedades com nomes que comecem ou terminem com um sublinhado ("_"). Isso é reservado para classes e propriedades do sistema.

Se a propriedade definida pela `Put` função existir na classe pai, o valor padrão da propriedade será alterado, a menos que o tipo de propriedade não corresponda ao tipo de classe pai. Se a propriedade não existir e não for uma incompatibilidade de tipos, a propriedade será criada.

Use o `vtType` parâmetro somente ao criar novas propriedades em uma definição de classe CIM `pVal` e `null` é ou aponta para `VARIANT` um de `VT_NULL`tipo. Nesse caso, o `vType` parâmetro especifica o tipo CIM da propriedade. Em todos os outros casos `vtType` , deve ser 0. `vtType`também deverá ser 0 se o objeto subjacente for uma instância (mesmo se `Val` for `null`) porque o tipo da propriedade é fixo e não pode ser alterado.

## <a name="example"></a>Exemplo

Para obter um exemplo, consulte o método [IWbemClassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .

## <a name="requirements"></a>Requisitos

**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).

**Cabeçalho:** WMINet_Utils.idl

**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
