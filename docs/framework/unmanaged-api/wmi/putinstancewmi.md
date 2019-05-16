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
ms.openlocfilehash: a9774656d010a3e52dd2392094ba6b529a573f3e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636559"
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
[in] Um ponteiro para a instância a ser gravado.

`lFlags`\
[in] Uma combinação de sinalizadores que afetam o comportamento dessa função. Os seguintes valores são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Se definido, WMI não armazena qualquer qualificador com a **Amended** sabor. <br> Se não for definido, supõe-se que esse objeto não está localizado, e todos os qualificadores são armazenados com essa instância. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Se ele não existir ou substituí-lo se ele já existir, crie a instância. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Atualize a instância. A instância deve existir para a chamada seja bem-sucedida. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Crie a instância. A chamada falhará se a instância já existe. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | O sinalizador faz com que uma chamada semissíncrona. |

`pCtx`\
[in] Normalmente, esse valor é `null`. Caso contrário, ele é um ponteiro para um [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instância que pode ser usada pelo provedor que está fornecendo as classes solicitadas.

`ppCallResult`\
[out] Se `null`, esse parâmetro é usado. Se `lFlags` contém `WBEM_FLAG_RETURN_IMMEDIATELY`, a função retornará imediatamente com `WBEM_S_NO_ERROR`. O `ppCallResult` parâmetro recebe um ponteiro para um novo [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) objeto.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | O usuário não tem permissão para atualizar uma instância da classe especificada. |
| `WBEM_E_FAILED` | 0x80041001 | Ocorreu um erro não especificado. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | A classe que dão suporte a essa instância não é válida. |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | uma `null` foi especificado para uma propriedade que não pode ser `null`, por exemplo, um que é marcado por um **indexado** ou **Not_Null** qualificador. |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | A instância especificada é inválida. (Por exemplo, chamar `PutInstanceWmi` com uma classe retorna esse valor.) |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | O `WBEM_FLAG_CREATE_ONLY` sinalizador foi especificado, mas a instância já existe. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` foi especificado no `lFlags`, mas a instância não existe. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI foi provavelmente interrompido e reiniciar. Chame [ConnectServerWmi](connectserverwmi.md) novamente. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | O link RPC (chamada) de procedimento remoto entre o processo atual e a WMI falhou. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida. |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) método.

O `PutInstanceWmi` função dá suporte à criação de instâncias e instâncias de classes existentes somente atualização.  Dependendo de como a `pCtx` parâmetro for definido, algumas ou todas as propriedades da instância são atualizadas.

Quando a instância apontado pelo `pInst` pertence a uma subclasse, gerenciamento do Windows chama todos os provedores de responsáveis para as classes da qual deriva a subclasse. Todos esses provedores devem obter êxito para o original `PutInstanceWmi` solicitação seja bem-sucedida. O provedor de suporte a classe de nível mais alta na hierarquia é chamado pela primeira vez. A ordem de chamada continua com a subclasse da classe superior e prossegue de cima para baixo até que o gerenciamento do Windows alcança o provedor para a classe que tem a instância apontada pelo `pInst`.
Gerenciamento do Windows não chama os provedores para qualquer uma das classes filhas de uma instância.

Quando um aplicativo deve atualizar uma instância que pertence a uma hierarquia de classe, o `pInst` parâmetro deve apontar para a instância que contém as propriedades a ser modificado. Ou seja, considere uma instância de destino que pertence a **ClassB**. O **ClassB** instância deriva **ClassA**, e **ClassA** define a propriedade **PropA**. Se um aplicativo quiser fazer uma alteração para o valor de **PropA** na **ClassB** instância, ele deve definir `pInst` para essa instância em vez de uma instância do **ClassA** .

Chamar `PutInstanceWmi` em uma instância de uma classe abstrata não é permitido.

Se a chamada de função falhar, você pode obter informações adicionais sobre erros chamando o [GetErrorInfo](geterrorinfo.md) função.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** WMINet_Utils.idl

**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
