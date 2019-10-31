---
title: Função PutClassWmi (referência de API não gerenciada)
description: A função PutClassWmi cria uma nova classe ou atualiza uma existente.
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 95a5e1f6339bde9dfe5c5ad9f989fc06e10fa7f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101784"
---
# <a name="putclasswmi-function"></a>Função PutClassWmi

Cria uma nova classe ou atualiza uma existente.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a>Parâmetros

`pObject`\
no Um ponteiro para uma definição de classe válida. Ele deve ser inicializado corretamente com todos os valores de propriedade necessários.

`lFlags`\
no Uma combinação de sinalizadores que afetam o comportamento dessa função. Os valores a seguir são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Se definido, o WMI não armazena nenhum qualificador com o tipo emendado. <br> Se não estiver definido, supõe-se que esse objeto não está localizado e todos os qualificadores são armazenados com essa instância. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Crie a classe se ela não existir ou substitua-a se ela já existir. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Atualize a classe. A classe deve existir para que a chamada seja bem-sucedida. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Crie a classe. A chamada falhará se a classe já existir. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | O sinalizador causa uma chamada de semisynchronous. |
| `WBEM_FLAG_OWNER_UPDATE` | 0x10000 | Os provedores de push devem especificar esse sinalizador ao chamar `PutClassWmi` para indicar que essa classe foi alterada. |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | 0 | Permite que uma classe seja atualizada se não houver classes derivadas e nenhuma instância dessa classe. Ele também permitirá atualizações em todos os casos se a alteração for apenas para qualificadores não importantes, como o qualificador de descrição. Se a classe tiver instâncias ou alterações para qualificadores importantes, a atualização falhará. |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | 0x20 | Permite atualizações de classes, mesmo se houver classes filhas, desde que a alteração não cause conflitos com classes filhas. Por exemplo, esse sinalizador permite que uma nova propriedade seja adicionada à classe base que não foi mencionada anteriormente em nenhuma das classes filhas. Se a classe tiver instâncias, a atualização falhará. |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | 0x40 | força atualizações de classes quando existem classes filhas conflitantes. Por exemplo, esse sinalizador força uma atualização se um qualificador de classe é definido em uma classe filho e a classe base tenta adicionar o mesmo qualificador que está em conflito com o existente. No modo de força, o conflito tis é resolvido com a exclusão do qualificador conflitante na classe filho. |

`pCtx`\
no Normalmente, esse valor é `null`. Caso contrário, é um ponteiro para uma instância de [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) que pode ser usada pelo provedor que está fornecendo as classes solicitadas.

`ppCallResult`\
fora Se `null`, esse parâmetro não será usado. Se `lFlags` contiver `WBEM_FLAG_RETURN_IMMEDIATELY`, a função retornará imediatamente com `WBEM_S_NO_ERROR`. O parâmetro `ppCallResult` recebe um ponteiro para um novo objeto [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) .

## <a name="return-value"></a>Valor retornado

Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | O usuário não tem permissão para criar ou modificar classes. |
| `WBEM_E_FAILED` | 0x80041001 | Ocorreu um erro não especificado. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | A classe especificada é inválida. Normalmente, isso indica que `pObject` especifica um objeto de instância. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
| `WBEM_E_INVALID OPERATION` | 0x80041016 | O nome de classe especificado não é válido. |
| `WBEM_E_CLASS_HAS_CHILDREN` | 0x80041025 | Foi feita uma tentativa de fazer uma alteração que invalidaria uma subclasse. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | O sinalizador de `WBEM_FLAG_CREATE_ONLY` foi especificado, mas a classe já existe. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` foi especificado em `lFlags`e a classe não foi encontrada. |
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | As propriedades obrigatórias para classes não foram definidas. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | O WMI provavelmente foi interrompido e reiniciado. Chame [ConnectServerWmi](connectserverwmi.md) novamente. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | O link RPC (chamada de procedimento remoto) entre o processo atual e o WMI falhou. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IWbemServices::P utclass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) .

O usuário não pode criar classes com nomes que comecem ou terminem com um caractere de sublinhado.

Se a chamada de função falhar, você poderá obter informações adicionais sobre o erro chamando a função [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

**Cabeçalho:** WMINet_Utils. idl

**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
