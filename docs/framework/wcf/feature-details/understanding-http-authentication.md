---
title: "Noções básicas de autenticação HTTP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9376309a-39e3-4819-b47b-a73982b57620
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8e1c299e58f83807689f71ded2dec569e6c70015
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="understanding-http-authentication"></a>Noções básicas de autenticação HTTP
A autenticação é o processo de identificar se um cliente tem permissão para acessar um recurso. O protocolo HTTP oferece suporte à autenticação como um meio de negociação de acesso a um recurso seguro.  
  
 A solicitação inicial de um cliente normalmente é uma solicitação anônima, não contém informações de autenticação. Aplicativos de servidor HTTP podem negar a solicitação anônima ao indicando que a autenticação é necessária. O aplicativo de servidor envia os cabeçalhos de autenticação da Web para indicar os esquemas de autenticação com suporte. Este documento descreve vários esquemas de autenticação para HTTP e discute o suporte em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="http-authentication-schemes"></a>Esquemas de autenticação HTTP  
 O servidor pode especificar vários esquemas de autenticação do cliente escolher. A tabela a seguir descreve alguns esquemas de autenticação geralmente encontrados em aplicativos do Windows.  
  
|Esquema de autenticação|Descrição|  
|---------------------------|-----------------|  
|Anônimo|Uma solicitação anônima não contém informações de autenticação. Isso é equivalente a conceder todos acesso ao recurso.|  
|Basic|Autenticação básica envia uma cadeia de caracteres codificada em Base64 que contém um nome de usuário e senha para o cliente. Base64 não é uma forma de criptografia e deve ser considerado igual a enviar o nome de usuário e senha em texto não criptografado. Se precisar de um recurso a ser protegida, considere fortemente usando um esquema de autenticação diferente da autenticação básica.|  
|Digest|A autenticação Digest é um esquema de desafio / resposta que substitui a autenticação básica. O servidor envia uma cadeia de caracteres dos dados aleatórios chamados um *nonce* ao cliente como um desafio. O cliente responde com um hash que inclui o nome de usuário, senha e nonce entre informações adicionais. A complexidade que apresenta este exchange e o hash de dados tornar mais difícil roubar e reutilizar as credenciais do usuário com esse esquema de autenticação.<br /><br /> A autenticação Digest requer o uso de contas de domínio do Windows. O resumo de *realm* é o nome de domínio do Windows. Portanto, você não pode usar um servidor em execução em um sistema operacional que não oferece suporte a domínios do Windows, como o Windows XP Home Edition, com a autenticação Digest. Por outro lado, quando o cliente é executado em um sistema operacional que não oferece suporte a domínios do Windows, uma conta de domínio deve ser explicitamente especificada durante a autenticação.|  
|NTLM|Autenticação NT LAN Manager (NTLM) é um esquema de desafio / resposta que é uma variação protegida da autenticação Digest. NTLM usa as credenciais do Windows para transformar os dados de desafio em vez da senha e nome de usuário sem codificação. A autenticação NTLM exige várias trocas entre o cliente e servidor. O servidor e todos os proxies intermediários devem oferecer suporte a conexões persistentes para concluir com êxito a autenticação.|  
|Negotiate|Negociar autenticação seleciona automaticamente entre o protocolo Kerberos e a autenticação NTLM, dependendo da disponibilidade. O protocolo Kerberos é usado se estiver disponível; Caso contrário, a tentativa de NTLM. A autenticação Kerberos aprimora significativamente NTLM. A autenticação Kerberos é mais rápido do que NTLM e permite o uso da autenticação mútua e a delegação de credenciais para computadores remotos.|  
|Windows Live ID|O serviço HTTP do Windows subjacente inclui a autenticação usando protocolos federados. No entanto, os transportes de HTTP padrão em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não suporta o uso de esquemas de autenticação federada, como Microsoft Windows Live ID. Suporte para esse recurso está disponível atualmente com o uso de segurança de mensagem. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Federação e Tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
## <a name="choosing-an-authentication-scheme"></a>Escolher um esquema de autenticação  
 Ao selecionar os possíveis esquemas de autenticação para um servidor HTTP, alguns itens a serem considerados incluem o seguinte:  
  
-   Considere se o recurso precisa ser protegido. Usando a autenticação HTTP requer a transmissão de dados mais e pode limitar a interoperabilidade com clientes. Permitir acesso anônimo aos recursos que não precisam ser protegidos.  
  
-   Se o recurso precisa ser protegida, considere quais esquemas de autenticação fornecem o nível de segurança necessário. O esquema padrão de autenticação mais fraco discutido aqui é a autenticação básica. Autenticação básica não protege as credenciais do usuário. O esquema mais forte de autenticação padrão é a autenticação Negotiate, resultando no protocolo Kerberos.  
  
-   Um servidor não deve apresentar (nos cabeçalhos de autenticação WWW) qualquer esquema que não está preparado para aceitar ou que não protege o recurso protegido adequadamente. Os clientes estão livres para escolher entre qualquer um dos esquemas de autenticação que apresenta o servidor. Alguns clientes como padrão um esquema de autenticação de baixa segurança ou o esquema de autenticação primeiro na lista do servidor.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de segurança de transporte](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 [Usando a representação com segurança de transporte](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)  
 [Delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
