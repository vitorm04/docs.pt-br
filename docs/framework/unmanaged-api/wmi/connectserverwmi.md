---
title: Função ConnectServerWmi (referência de API não gerenciada)
description: A função ConnectServerWmi usa DCOM para criar uma conexão com um namespace WMI.
ms.date: 11/06/2017
api_name:
- ConnectServerWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ConnectServerWmi
helpviewer_keywords:
- ConnectServerWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 25a73060ed242fd0e77042cd0ea9618b9b27250f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128687"
---
# <a name="connectserverwmi-function"></a>Função ConnectServerWmi

Cria uma conexão por meio do DCOM para um namespace do WMI em um computador especificado.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT ConnectServerWmi (
   [in] BSTR               strNetworkResource,
   [in] BSTR               strUser,
   [in] BSTR               strPassword,
   [in] BSTR               strLocale,
   [in] long               lSecurityFlags,
   [in] BSTR               strAuthority,
   [in] IWbemContext*      pCtx,
   [out] IWbemServices**   ppNamespace,
   [in] DWORD              impLevel,
   [in] DWORD              authLevel
);
```

## <a name="parameters"></a>Parâmetros

`strNetworkResource`\
no Ponteiro para um `BSTR` válido que contém o caminho do objeto do namespace WMI correto. Consulte a seção [comentários](#remarks) para obter mais informações.

`strUser`\
no Um ponteiro para um `BSTR` válido que contém o nome de usuário. Um valor `null` indica o contexto de segurança atual. Se o usuário for de um domínio diferente do atual, `strUser` também poderá conter o domínio e o nome de usuário separados por uma barra invertida. `strUser` também pode estar no formato UPN (nome principal do usuário), como `userName@domainName`. Consulte a seção [comentários](#remarks) para obter mais informações.

`strPassword`\
no Um ponteiro para um `BSTR` válido que contém a senha. Um `null` indica o contexto de segurança atual. Uma cadeia de caracteres vazia ("") indica uma senha de comprimento zero válida.

`strLocale`\
no Um ponteiro para um `BSTR` válido que indica a localidade correta para a recuperação de informações. Para identificadores de localidade da Microsoft, o formato da cadeia de caracteres é "MS\_*xxx*", em que *xxx* é uma cadeia de caracteres no formato HEXADECIMAL que indica o LCID (identificador de localidade). Se uma localidade inválida for especificada, o método retornará `WBEM_E_INVALID_PARAMETER`, exceto no Windows 7, em que a localidade padrão do servidor será usada. Se ' null1 ', a localidade atual será usada.

`lSecurityFlags`\
no Sinalizadores a serem passados para o método de `ConnectServerWmi`. Um valor de zero (0) para esse parâmetro resulta na chamada para `ConnectServerWmi` retornando somente depois que uma conexão com o servidor é estabelecida. Isso pode resultar em um aplicativo não respondendo indefinidamente se o servidor estiver interrompido. Os outros valores válidos são:

| Constante  | Valor  | Descrição  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | Reservado para uso interno. Não use. |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi` retorna em dois minutos ou menos. |

`strAuthority`\
no O nome de domínio do usuário. Ele pode ter os seguintes valores:

| Valor | Descrição |
|---------|---------|
| Ficará | A autenticação NTLM é usada e o domínio NTLM do usuário atual é usado. Se `strUser` especificar o domínio (o local recomendado), ele não deverá ser especificado aqui. A função retornará `WBEM_E_INVALID_PARAMETER` se você especificar o domínio em ambos os parâmetros. |
| Kerberos:*nome da entidade* | A autenticação Kerberos é usada e esse parâmetro contém um nome de entidade de segurança Kerberos. |
| NTLMDOMAIN:*nome de domínio* | A autenticação do Gerenciador de LAN do NT é usada e esse parâmetro contém um nome de domínio NTLM. |

`pCtx`\
no Normalmente, esse parâmetro é `null`. Caso contrário, é um ponteiro para um objeto [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) exigido por um ou mais provedores de classe dinâmica.

`ppNamespace`\
fora Quando a função retorna, recebe um ponteiro para um objeto [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) associado ao namespace especificado. Ele é definido para apontar para `null` quando há um erro.

`impLevel`\
no O nível de representação.

`authLevel`\
no O nível de autorização.

## <a name="return-value"></a>Valor retornado

Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Houve uma falha geral. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IWbemLocator:: ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) .

Para acesso local ao namespace padrão, `strNetworkResource` pode ser um caminho de objeto simples: "root\default" ou "\\.\root\default". Para acessar o namespace padrão em um computador remoto usando a rede compatível COM ou COM a Microsoft, inclua o nome do computador: "\\myserver\root\default". O nome do computador também pode ser um nome DNS ou endereço IP. A função `ConnectServerWmi` também pode se conectar a computadores que executam o IPv6 usando um endereço IPv6.

`strUser` não pode ser uma cadeia de caracteres vazia. Se o domínio for especificado em `strAuthority`, ele também não deverá ser incluído em `strUser`ou a função retornará `WBEM_E_INVALID_PARAMETER`.

## <a name="requirements"></a>Requisitos

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

 **Cabeçalho:** WMINet_Utils. idl

 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
