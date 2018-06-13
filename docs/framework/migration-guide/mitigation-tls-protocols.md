---
title: 'Mitigação: protocolos TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5d37326d0278225146d217624508e7c7738375b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388255"
---
# <a name="mitigation-tls-protocols"></a>Mitigação: protocolos TLS
A partir do .NET Framework 4.6, as classes <xref:System.Net.ServicePointManager?displayProperty=nameWithType> e <xref:System.Net.Security.SslStream?displayProperty=nameWithType> têm permissão para usar um dos três protocolos a seguir: Tls1.0, Tls1.1 ou Tls 1.2. Não há suporte para o protocolo SSL 3.0 e a criptografia RC4.  
  
## <a name="impact"></a>Impacto  
 Essa alteração afeta:  
  
-   Qualquer aplicativo que usa o SSL para se comunicar com um servidor HTTPS ou um servidor de soquete usando qualquer um dos seguintes tipos: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient> e <xref:System.Net.Security.SslStream>.  
  
-   Qualquer aplicativo do lado do servidor que não possa ser atualizado para dar suporte ao Tls1.0, Tls1.1 ou Tls 1.2.  
  
## <a name="mitigation"></a>Redução  
 A mitigação recomendada é fazer upgrade do aplicativo do lado do servidor para Tls1.0, Tls1.1 ou Tls 1.2. Se não for viável ou se os aplicativos cliente estiverem desfeitos, a classe <xref:System.AppContext> poderá ser usada para recusar esse recurso de duas maneiras:  
  
-   De modo programático, usando um trecho de código como o seguinte:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     Como o objeto <xref:System.Net.ServicePointManager> foi inicializado apenas uma vez, definir essas configurações de compatibilidade deverá ser a primeira coisa que o aplicativo fará.  
  
-   Adicionando a seguinte linha à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo app.config:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 No entanto, observe que não é recomendável recusar o comportamento padrão, pois isso torna o aplicativo menos seguro.  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
