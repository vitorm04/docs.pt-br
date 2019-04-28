---
title: Noções básicas de autenticação HTTP
ms.date: 03/30/2017
ms.assetid: 9376309a-39e3-4819-b47b-a73982b57620
ms.openlocfilehash: 430b0ddb98514b605178124f331e5152605a2b89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918899"
---
# <a name="understanding-http-authentication"></a>Noções básicas de autenticação HTTP
A autenticação é o processo de identificar se um cliente está qualificado para acessar um recurso. O protocolo HTTP oferece suporte à autenticação como um meio de negociar o acesso a um recurso seguro.  
  
 A solicitação inicial de um cliente normalmente é uma solicitação anônima, o que não contêm informações de autenticação. Aplicativos de servidor HTTP podem negar a solicitação anônima ao mesmo tempo, indicando que a autenticação é necessária. O aplicativo de servidor envia cabeçalhos de autenticação de WWW para indicar os esquemas de autenticação com suporte. Este documento descreve vários esquemas de autenticação para HTTP e discute o suporte no Windows Communication Foundation (WCF).  
  
## <a name="http-authentication-schemes"></a>Esquemas de autenticação HTTP  
 O servidor pode especificar vários esquemas de autenticação para o cliente à sua escolha. A tabela a seguir descreve alguns dos esquemas de autenticação geralmente encontrados em aplicativos do Windows.  
  
|Esquema de autenticação|Descrição|  
|---------------------------|-----------------|  
|Anônimo|Uma solicitação anônima não contém informações de autenticação. Isso é equivalente a conceder todas as pessoas acesso ao recurso.|  
|Basic|Autenticação básica envia uma cadeia de caracteres codificada em Base64 que contém um nome de usuário e senha para o cliente. Base64 não é uma forma de criptografia e deve ser considerado o mesmo que enviar o nome de usuário e senha em texto não criptografado. Se um recurso precisa ser protegido, considere seriamente o uso de um esquema de autenticação diferente da autenticação básica.|  
|Digest|A autenticação Digest é um esquema de desafio / resposta que se destina a substituir a autenticação básica. O servidor envia uma cadeia de caracteres de dados aleatórios chamados um *nonce* ao cliente como um desafio. O cliente responde com um hash que inclui o nome de usuário, senha e nonce entre informações adicionais. A complexidade que introduz essa troca e o hash de dados torna mais difícil roubar e reutilizar as credenciais do usuário com esse esquema de autenticação.<br /><br /> A autenticação Digest requer o uso de contas de domínio do Windows. O resumo da mensagem *realm* é o nome de domínio do Windows. Portanto, é possível usar um servidor executando em um sistema operacional que não oferece suporte a domínios do Windows, como o Windows XP Home Edition, com a autenticação Digest. Por outro lado, quando o cliente é executado em um sistema operacional que não oferece suporte a domínios do Windows, uma conta de domínio deve ser explicitamente especificada durante a autenticação.|  
|NTLM|Autenticação NT LAN Manager (NTLM) é um esquema de desafio / resposta que é uma variação protegida da autenticação Digest. NTLM usa as credenciais do Windows para transformar os dados de desafio em vez do nome de usuário sem codificação e a senha. A autenticação NTLM exige várias trocas entre o cliente e servidor. O servidor e todos os proxies intermediários devem dar suporte a conexões persistentes para concluir com êxito a autenticação.|  
|Negotiate|Negociar autenticação seleciona automaticamente entre o protocolo Kerberos e a autenticação NTLM, dependendo da disponibilidade. O protocolo Kerberos é usado se ele estiver disponível; Caso contrário, a tentativa de NTLM. A autenticação Kerberos melhora significativamente o após a NTLM. A autenticação Kerberos é mais rápido do que o NTLM e permite o uso da autenticação mútua e delegação de credenciais em computadores remotos.|  
|Windows Live ID|O serviço do Windows HTTP subjacente inclui a autenticação usando protocolos federados. No entanto, os transportes HTTP padrão no WCF não têm suporte para o uso de esquemas de autenticação federada, como o Microsoft Windows Live ID. Suporte para esse recurso está disponível atualmente com o uso de segurança de mensagem. Para obter mais informações, consulte [federação e Tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
## <a name="choosing-an-authentication-scheme"></a>Escolher um esquema de autenticação  
 Ao selecionar os possíveis esquemas de autenticação para um servidor HTTP, alguns itens a serem considerados incluem o seguinte:  
  
- Considere se o recurso precisa ser protegido. Usando a autenticação HTTP requer a transmissão de dados mais e pode limitar a interoperabilidade com clientes. Permitir acesso anônimo a recursos que não precisam ser protegidos.  
  
- Se o recurso precisa ser protegido, considere quais esquemas de autenticação fornecem o nível de segurança necessário. O esquema de autenticação padrão mais fraco discutido aqui é a autenticação básica. Autenticação básica não protege as credenciais do usuário. O esquema padrão de autenticação mais forte é a autenticação Negotiate, resultando no protocolo Kerberos.  
  
- Um servidor não deve representar (nos cabeçalhos de autenticação de WWW) qualquer esquema que não está preparada para aceitar ou que não protege o recurso protegido adequadamente. Os clientes são livres para escolher entre qualquer um dos esquemas de autenticação que o servidor apresenta. Alguns clientes usam como padrão um esquema de autenticação fraca ou o esquema de autenticação primeiro na lista do servidor.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de segurança de transporte](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)
- [Usando a representação com segurança de transporte](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)
- [Delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
