---
title: Função ExecNotificationQueryWmi (referência de API não gerenciada)
description: A função ExecNotificationQueryWmi executa uma consulta para receber eventos.
ms.date: 11/06/2017
api_name:
- ExecNotificationQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecNotificationQueryWmi
helpviewer_keywords:
- ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cfe54c7c9b7ae707b2d3591afbd830bac171f0b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798652"
---
# <a name="execnotificationquerywmi-function"></a>Função ExecNotificationQueryWmi

Executa uma consulta para receber eventos. A chamada retorna imediatamente, e o chamador pode sondar o enumerador retornado em busca de eventos à medida que eles chegam. A liberação do enumerador retornado cancela a consulta.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT ExecNotificationQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
);
```

## <a name="parameters"></a>Parâmetros

`strQueryLanguage`\
no Uma cadeia de caracteres com a linguagem de consulta válida com suporte pelo gerenciamento do Windows. Deve ser "WQL", o acrônimo para linguagem WQL.

`strQuery`\
no O texto da consulta. O parâmetro não pode ser `null`.

`lFlags`\
no Uma combinação dos dois sinalizadores a seguir que afetam o comportamento dessa função. Esses valores são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código.

| Constante | Valor  | Descrição  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | O sinalizador causa uma chamada de semisynchronous. Se esse sinalizador não for definido, a chamada falhará. Isso ocorre porque os eventos são recebidos continuamente, o que significa que o usuário deve sondar o enumerador retornado. Bloquear essa chamada indefinidamente torna isso impossível. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | A função retorna um enumerador somente encaminhamento. Normalmente, enumeradores somente de encaminhamento são mais rápidos e usam menos memória do que enumeradores convencionais, mas não permitem que as chamadas [clonem](clone.md). |

`pCtx`\
no Normalmente, esse valor é `null`. Caso contrário, é um ponteiro para uma instância de [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) que pode ser usada pelo provedor que está fornecendo os eventos solicitados.

`ppEnum`\
fora Se nenhum erro ocorrer, o receberá o ponteiro para o enumerador que permite ao chamador recuperar as instâncias no conjunto de resultados da consulta. Consulte a seção [comentários](#remarks) para obter mais informações.

`authLevel`\
no O nível de autorização.

`impLevel`\
no O nível de representação.

`pCurrentNamespace`\
no Um ponteiro para um objeto [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) que representa o namespace atual.

`strUser`\
no O nome de usuário. Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.

`strPassword`\
no A senha. Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.

`strAuthority`\
no O nome de domínio do usuário. Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.

## <a name="return-value"></a>Valor retornado

Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | O usuário não tem permissão para exibir uma ou mais das classes que a função pode retornar. |
| `WBEM_E_FAILED` | 0x80041001 | Ocorreu um erro não especificado. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | A consulta especifica uma classe que não existe. |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | 0x80042002 | Foi solicitada muita precisão na entrega de eventos. Uma tolerância de sondagem maior deve ser especificada. |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | 0x80042001 | A consulta solicita mais informações do que o gerenciamento do Windows pode fornecer. Isso `HRESULT` é retornado quando uma consulta de evento resulta em uma solicitação para sondar todos os objetos em um namespace. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | A consulta tinha um erro de sintaxe. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | O idioma de consulta solicitado não tem suporte. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | A consulta é muito complexa. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | O WMI provavelmente foi interrompido e reiniciado. Chame [ConnectServerWmi](connectserverwmi.md) novamente. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | O link RPC (chamada de procedimento remoto) entre o processo atual e o WMI falhou. |
| `WBEM_E_UNPARSABLE_QUERY` | 0x80041058 | A consulta não pode ser analisada. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IWbemServices:: ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) .

Depois que a função retorna, o chamador passa periodicamente `ppEnum` o objeto retornado para a [próxima](next.md) função para ver se há algum evento disponível.

Há limites para o número de `AND` palavras-chave e `OR` que podem ser usadas em consultas WQL. Grandes números de palavras-chave WQL usadas em uma consulta complexa podem fazer com que o WMI `WBEM_E_QUOTA_VIOLATION` retorne o código de erro (ou `HRESULT` 0x8004106c) como um valor. O limite de palavras-chave WQL depende da complexidade da consulta.

Se a chamada de função falhar, você poderá obter informações adicionais sobre o erro chamando a função [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Requisitos

**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).

**Cabeçalho:** WMINet_Utils.idl

**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
