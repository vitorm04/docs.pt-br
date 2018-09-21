---
title: Função ConnectServerWmi (referência de API não gerenciada)
description: A função ConnectServerWmi usa DCOM para criar uma conexão a um namespace WMI.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 244df48606f6d971d6b6e246c4f9b73f916cbdcd
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537102"
---
# <a name="connectserverwmi-function"></a>Função ConnectServerWmi
Cria uma conexão por meio do DCOM para um namespace do WMI em um computador especificado.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
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

`strNetworkResource` [in] Ponteiro para um válido `BSTR` que contém o caminho do objeto do namespace WMI correto. Consulte a [comentários](#remarks) seção para obter mais informações.

`strUser` [in] Um ponteiro para um válido `BSTR` que contém o nome de usuário. Um `null` valor indica o contexto de segurança atual. Se o usuário for de um domínio diferente daquele atual, `strUser` também pode conter o nome de usuário e domínio separados por uma barra invertida. `strUser` também pode ser no formato de nome principal (UPN) do usuário, tal como `userName@domainName`. Consulte a [comentários](#remarks) seção para obter mais informações.

`strPassword` [in] Um ponteiro para um válido `BSTR` que contém a senha. Um `null` indica o contexto de segurança atual. Uma cadeia de caracteres vazia ("") indica uma senha válida de comprimento zero.

`strLocale` [in] Um ponteiro para um válido `BSTR` que indica a localidade correta para a recuperação de informações. Identificadores de localidade da Microsoft, o formato da cadeia de caracteres é "MS\_*xxx*", onde *xxx* é uma cadeia de caracteres em formato hexadecimal que indica o identificador de localidade (LCID). Se um local inválido for especificado, o método retorna `WBEM_E_INVALID_PARAMETER` exceto no Windows 7, em que a localidade padrão do servidor é usada em vez disso. Se ' null1, a localidade atual é usado. 
 
`lSecurityFlags` [in] Sinalizadores a serem passados para o `ConnectServerWmi` método. Um valor de zero (0) para esse parâmetro resulta na chamada para `ConnectServerWmi` retornando somente após o estabelecimento de uma conexão ao servidor. Isso pode resultar em um aplicativo não está respondendo indefinidamente se o servidor será interrompido. Os outros valores válidos são:

| Constante  | Valor  | Descrição  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | Reservado para uso interno. Não use. |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi` Retorna em dois minutos ou menos. |

`strAuthority` [in] O nome de domínio do usuário. Ele pode ter os seguintes valores:

| Valor | Descrição |
|---------|---------|
| em branco | A autenticação NTLM é usada e o domínio NTLM do usuário atual será usado. Se `strUser` Especifica o domínio (o local recomendado), ele não deve ser especificado aqui. A função retorna `WBEM_E_INVALID_PARAMETER` se você especificar o domínio em ambos os parâmetros. |
| Kerberos:*nome da entidade* | A autenticação Kerberos é usada, e este parâmetro contém um nome principal Kerberos. |
| NTLMDOMAIN:*nome de domínio* | Autenticação NT LAN Manager é usada, e este parâmetro contém um nome de domínio do NTLM. |

`pCtx`   
[in] Normalmente, esse parâmetro é é `null`. Caso contrário, ele é um ponteiro para um [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) objeto exigido por um ou mais provedores de classe dinâmica. 

`ppNamespace`  
[out] Quando a função retornar, recebe um ponteiro para um [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objeto associado ao namespace especificado. Ele é definido para apontar para `null` quando ocorre um erro.

`impLevel`  
[in] O nível de representação.

`authLevel`  
[in] O nível de autorização.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Houve uma falha geral. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) método.

 Para acesso local para o namespace padrão, `strNetworkResource` pode ser um caminho de objeto simples: "root\default" ou "\\.\root\default". Para acessar o namespace padrão em um computador remoto usando a rede COM ou compatível com a Microsoft, que incluem o nome do computador: "\\myserver\root\default". O nome do computador também pode ser um nome DNS ou endereço IP. O `ConnectServerWmi` função também pode se conectar com computadores que executam o IPv6 usando um endereço IPv6.

`strUser` não pode ser uma cadeia de caracteres vazia. Se o domínio é especificado na `strAuthority`, ela também não deve ser incluída no `strUser`, ou a função retornará `WBEM_E_INVALID_PARAMETER`.


## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
