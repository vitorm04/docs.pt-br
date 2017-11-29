---
title: "Função ConnectServerWmi (referência de API não gerenciada)"
description: "A função ConnectServerWmi usa DCOM para criar uma conexão a um namespace do WMI."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ConnectServerWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ConnectServerWmi
helpviewer_keywords: ConnectServerWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b51050bce4603ebcfe99fb38d66e54683c677293
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
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

`strNetworkResource`[in] Ponteiro para um válida `BSTR` que contém o caminho do namespace WMI correto. Consulte o [comentários](#remarks) para obter mais informações.

`strUser`[in] Um ponteiro para um válida `BSTR` que contém o nome de usuário. Um `null` valor indica o contexto de segurança atual. Se o usuário for de um domínio diferente do ano atual, `strUser` também pode conter o nome de usuário e domínio separado por uma barra invertida. `strUser`pode também ser usuário nome principal (UPN) Formatar, suhc como  *userName@domainName* . Consulte o [comentários](#remarks) para obter mais informações.

`strPassword`[in] Um ponteiro para um válida `BSTR` que contém a senha. A `null` indica o contexto de segurança atual. Uma cadeia de caracteres vazia ("") indica uma senha válida de comprimento zero.

`strLocale`[in] Um ponteiro para um válida `BSTR` que indica o local correto para recuperação de informações. Identificadores de localidade da Microsoft, o formato da cadeia de caracteres é "MS\_*xxx*", onde *xxx* é uma cadeia de caracteres em formato hexadecimal que indica o identificador de localidade (LCID). Se for especificado um local inválido, o método retorna `WBEM_E_INVALID_PARAMETER` , exceto no Windows 7, em que a localidade padrão do servidor é usada em vez disso. Se ' null1, a localidade atual é usado. 
 
`lSecurityFlags`[in] Sinalizadores para passar para o `ConnectServerWmi` método. Um valor de zero (0) para esse parâmetro resulta na chamada para `ConnectServerWmi` retornando somente depois que uma conexão com o servidor é estabelecida. Isso pode resultar em um aplicativo não está respondendo indefinidamente se o servidor será interrompido. Os outros valores válidos são:

| Constante  | Valor  | Descrição  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | Reservado para uso interno. Não use. |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi`Retorna em dois minutos ou menos. |

`strAuthority`[in] O nome de domínio do usuário. Ele pode ter os seguintes valores:

| Valor | Descrição |
|---------|---------|
| Em branco | A autenticação NTLM é usada e o domínio NTLM do usuário atual será usado. Se `strUser` Especifica o domínio (o local recomendado), ele não deve ser especificado aqui. A função retorna `WBEM_E_INVALID_PARAMETER` se você especificar o domínio em ambos os parâmetros. |
| Kerberos:*nome principal* | A autenticação Kerberos é usada e este parâmetro contém um nome principal Kerberos. |
| NTLMDOMAIN:*nome de domínio* | Autenticação NT LAN Manager é usada e este parâmetro contém um nome de domínio NTLM. |

`pCtx`   
[in] Normalmente, esse parâmetro é `null`. Caso contrário, é um ponteiro para um [IWbemContext](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx) objeto exigido por um ou mais provedores de classe dinâmica. 

`ppNamespace`  
[out] Quando a função retornar, recebe um ponteiro para um [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objeto associado ao namespace especificado. Ele é definido para apontar para `null` quando há um erro.

`impLevel`  
[in] O nível de representação.

`authLevel`  
[in] O nível de autorização.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Houve uma falha geral. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória suficiente está disponível para concluir a operação. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) método.

 Para acesso local ao namespace padrão, `strNetworkResource` pode ser um caminho de objeto simples: "root\default" ou "\\.\root\default". Para acessar o namespace padrão em um computador remoto usando redes COM ou compatível com a Microsoft, que incluem o nome do computador: "\\myserver\root\default". O nome do computador também pode ser um nome DNS ou endereço IP. O `ConnectServerWmi` função também pode se conectar com computadores que executam o IPv6 usando um endereço IPv6.

`strUser`não pode ser uma cadeia de caracteres vazia. Se o domínio for especificado em `strAuthority`, ela também não deve ser incluída no `strUser`, ou a função retornará `WBEM_E_INVALID_PARAMETER`.


## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
