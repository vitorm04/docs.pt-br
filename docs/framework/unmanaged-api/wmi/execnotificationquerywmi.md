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
ms.openlocfilehash: 9cac00ff96d0c7007bdd6135282c3f767217385e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352874"
---
# <a name="execnotificationquerywmi-function"></a>Função ExecNotificationQueryWmi

Executa uma consulta para receber eventos. A chamada retorna imediatamente, e o chamador pode sondar o enumerador retornado para eventos à medida que eles chegam. Liberar enumerador retornado cancela a consulta.

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
[in] Uma cadeia de caracteres com a linguagem de consulta válida com suporte pelo gerenciamento do Windows. Ele deve ser "WQL", o acrônimo de linguagem de consulta WMI.

`strQuery`\
[in] O texto da consulta. O parâmetro não pode ser `null`.

`lFlags`\
[in] Uma combinação dos seguintes dois sinalizadores que afetam o comportamento dessa função. Esses valores são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código.

| Constante | Valor  | Descrição  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | O sinalizador faz com que uma chamada semissíncrona. Se este sinalizador não for definido, a chamada falhará. Isso é porque os eventos são recebidos continuamente, que significa que o usuário deve sondar o enumerador retornado. Essa chamada de bloqueio por tempo indeterminado, que torna impossível. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | A função retorna um enumerador de somente avanço. Normalmente, os enumeradores de somente avanço são mais rápidos e usam menos memória do que os enumeradores convencionais, mas eles não permitem chamadas para [Clone](clone.md). |

`pCtx`\
[in] Normalmente, esse valor é `null`. Caso contrário, ele é um ponteiro para um [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instância que pode ser usada pelo provedor que está fornecendo os eventos solicitados.

`ppEnum`\
[out] Se nenhum erro ocorrer, recebe o ponteiro para o enumerador que permite que o chamador recuperar as instâncias no conjunto de resultados da consulta. Consulte a [comentários](#remarks) seção para obter mais informações.

`authLevel`\
[in] O nível de autorização.

`impLevel`\
[in] O nível de representação.

`pCurrentNamespace`\
[in] Um ponteiro para um [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objeto que representa o namespace atual.

`strUser`\
[in] O nome de usuário. Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.

`strPassword`\
[in] A senha. Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.

`strAuthority`\
[in] O nome de domínio do usuário. Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | O usuário não tem permissão para exibir um ou mais das classes que a função pode retornar. |
| `WBEM_E_FAILED` | 0x80041001 | Ocorreu um erro não especificado. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | A consulta especifica uma classe que não existe. |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | 0x80042002 | Muita precisão na entrega de eventos foi solicitada. Uma maior tolerância de sondagem deve ser especificada. |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | 0x80042001 | A consulta solicita mais informações do que o gerenciamento do Windows pode fornecer. Isso `HRESULT` é retornado quando uma consulta de evento resulta em uma solicitação de sondagem de todos os objetos em um namespace. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | A consulta teve um erro de sintaxe. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | O idioma de consulta solicitado não tem suporte. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | A consulta é muito complexa. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI foi provavelmente interrompido e reiniciar. Chame [ConnectServerWmi](connectserverwmi.md) novamente. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | O link RPC (chamada) de procedimento remoto entre o processo atual e a WMI falhou. |
| `WBEM_E_UNPARSABLE_QUERY` | 0x80041058 | A consulta não pode ser analisada. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) método.

Depois que a função retornar, o chamador periodicamente passa retornado `ppEnum` do objeto para o [próxima](next.md) função para ver se todos os eventos estão disponíveis.

Há limites para o número de `AND` e `OR` palavras-chave que podem ser usadas em consultas WQL. Grande número de palavras-chave WQL usadas em uma consulta complexa pode fazer com que o WMI retornar os `WBEM_E_QUOTA_VIOLATION` (ou 0x8004106c) código de erro como um `HRESULT` valor. O limite de palavras-chave WQL depende complexas como a consulta é.

Se a chamada de função falhar, você pode obter informações adicionais sobre erros chamando o [GetErrorInfo](geterrorinfo.md) função.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** WMINet_Utils.idl

**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)