---
title: Função PutInstanceWmi (referência de API não gerenciada)
description: A função PutInstanceWmi cria ou atualiza uma instância de uma classe existente.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37810ecab2e02d4ec250dd2a4b2657c3b898f714
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798379"
---
# <a name="putinstancewmi-function"></a>Função PutInstanceWmi

Cria ou atualiza uma instância de uma classe existente. A instância é gravada no repositório da WMI.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a>Parâmetros

`pInst`\
no Um ponteiro para a instância a ser gravada.

`lFlags`\
no Uma combinação de sinalizadores que afetam o comportamento dessa função. Os valores a seguir são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Se definido, o WMI não armazena nenhum qualificador com o tipo **emendado** . <br> Se não estiver definido, supõe-se que esse objeto não está localizado e todos os qualificadores são armazenados com essa instância. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Crie a instância se ela não existir ou substitua-a se ela já existir. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Atualize a instância. A instância deve existir para que a chamada seja bem-sucedida. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Crie a instância. A chamada falhará se a instância já existir. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | O sinalizador causa uma chamada de semisynchronous. |

`pCtx`\
no Normalmente, esse valor é `null`. Caso contrário, é um ponteiro para uma instância de [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) que pode ser usada pelo provedor que está fornecendo as classes solicitadas.

`ppCallResult`\
fora Se `null`, esse parâmetro não será usado. Se `lFlags` contiver `WBEM_FLAG_RETURN_IMMEDIATELY`, a função retornará imediatamente `WBEM_S_NO_ERROR`com. O `ppCallResult` parâmetro recebe um ponteiro para um novo objeto [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) .

## <a name="return-value"></a>Valor retornado

Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | O usuário não tem permissão para atualizar uma instância da classe especificada. |
| `WBEM_E_FAILED` | 0x80041001 | Ocorreu um erro não especificado. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | A classe que dá suporte a esta instância não é válida. |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | um `null` foi especificado para uma propriedade que não pode `null`ser, como uma que está marcada por um qualificador **indexado** ou **NOT_NULL** . |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | A instância especificada é inválida. (Por exemplo, chamar `PutInstanceWmi` com uma classe retorna esse valor.) |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | O `WBEM_FLAG_CREATE_ONLY` sinalizador foi especificado, mas a instância já existe. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY`foi especificado em `lFlags`, mas a instância não existe. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | O WMI provavelmente foi interrompido e reiniciado. Chame [ConnectServerWmi](connectserverwmi.md) novamente. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | O link RPC (chamada de procedimento remoto) entre o processo atual e o WMI falhou. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida. |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IWbemServices::P utinstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) .

A `PutInstanceWmi` função dá suporte à criação de instâncias e à atualização de instâncias somente de classes existentes.  Dependendo de como o `pCtx` parâmetro é definido, algumas ou todas as propriedades da instância serão atualizadas.

Quando a instância apontada `pInst` pertence a uma subclasse, o gerenciamento do Windows chama todos os provedores responsáveis pelas classes das quais a subclasse deriva. Todos esses provedores devem ter sucesso para que a `PutInstanceWmi` solicitação original seja realizada com sucesso. O provedor que dá suporte à classe mais alta na hierarquia é chamado primeiro. A ordem de chamada continua com a subclasse da classe superior e prossegue de cima para baixo até que o gerenciamento do Windows atinja o provedor para a classe proprietária da instância apontada `pInst`pelo.
O gerenciamento do Windows não chama os provedores para nenhuma das classes filhas de uma instância.

Quando um aplicativo deve atualizar uma instância que pertence a uma hierarquia de classe, `pInst` o parâmetro deve apontar para a instância que contém as propriedades a serem modificadas. Ou seja, considere uma instância de destino que pertença a **ClassB**. A instância **ClassB** deriva de **ClasseA**, e a **ClasseA** define a propriedade **Propa**. Se um aplicativo quiser fazer uma alteração no valor de **Propa** na instância de **ClassB** , ele deverá definir `pInst` essa instância em vez de uma instância de **ClassA**.

Não `PutInstanceWmi` é permitido chamar em uma instância de uma classe abstrata.

Se a chamada de função falhar, você poderá obter informações adicionais sobre o erro chamando a função [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Requisitos

**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).

**Cabeçalho:** WMINet_Utils.idl

**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
