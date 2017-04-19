---
title: "Mitigação: protocolos TLS | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1474aeb0e1be38018f9d27c49e8711800ecb9f01
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-tls-protocols"></a>Mitigação: protocolos TLS
A partir do .NET Framework 4.6, as classes <xref:System.Net.ServicePointManager?displayProperty=fullName> e <xref:System.Net.Security.SslStream?displayProperty=fullName> têm permissão para usar um destes três protocolos: Tls1.0, Tls1.1 ou Tls 1.2. Não há suporte para o protocolo SSL 3.0 e a criptografia RC4.  
  
## <a name="impact"></a>Impacto  
 Essa alteração afeta:  
  
-   Qualquer aplicativo que use SSL para se comunicar com um servidor HTTPS ou um servidor de soquete que usa um dos seguintes tipos: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient> e <xref:System.Net.Security.SslStream>.  
  
-   Qualquer aplicativo do lado do servidor que não possa ser atualizado para dar suporte ao Tls1.0, Tls1.1 ou Tls 1.2..  
  
## <a name="mitigation"></a>Redução  
 A mitigação recomendada é fazer upgrade do aplicativo do lado do servidor para Tls1.0, Tls1.1 ou Tls 1.2. Se não for viável, ou se os aplicativos do cliente estiverem interrompidos, a classe <xref:System.AppContext> poderá ser usada para recusar esse recurso de duas maneiras:  
  
-   De modo programático, usando um trecho de código como o seguinte:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     Como o objeto <xref:System.Net.ServicePointManager> foi inicializado apenas uma vez, definir essas configurações de compatibilidade deve ser a primeira tarefas do aplicativo.  
  
-   Adicionando a seguinte linha à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo app.config:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 No entanto, observe que não é recomendável recusar o comportamento padrão, pois isso torna o aplicativo menos seguro.  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
