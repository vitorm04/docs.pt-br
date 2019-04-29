---
title: Exemplo de segurança de descoberta
ms.date: 03/30/2017
ms.assetid: b8db01f4-b4a1-43fe-8e31-26d4e9304a65
ms.openlocfilehash: e956b9f8162d55891233a3ab664b05658d50eeab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772992"
---
# <a name="discovery-security-sample"></a>Exemplo de segurança de descoberta
A especificação de descoberta não requer que os pontos de extremidade que participam do processo de descoberta para ser seguro. Aprimorando as mensagens de descoberta com segurança atenua os vários tipos de ataques (negação de serviço, a alteração da mensagem, reproduzir, falsificação). Este exemplo implementa canais personalizados de computação e verifique se as assinaturas de mensagem usando o formato de assinatura compact (descrito na seção 8.2 da especificação WS-Discovery). O exemplo dá suporte a ambos os [especificação de descoberta de 2005](https://go.microsoft.com/fwlink/?LinkId=177912) e o [versão 1.1](https://go.microsoft.com/fwlink/?LinkId=179677).  
  
 O canal personalizado é aplicado no topo da pilha de canal existente para pontos de extremidade de descoberta e o anúncio. Dessa forma, um cabeçalho de assinatura é aplicado a todas as mensagens enviadas. A assinatura é verificada nas mensagens recebidas e quando ele não corresponde, ou quando as mensagens não tem uma assinatura, as mensagens serão descartadas. Para assinar e verificar as mensagens, o exemplo usa certificados.  
  
## <a name="discussion"></a>Discussão  
 O WCF é muito extensível e permite que os usuários a possibilidade de personalizar canais conforme desejado. O exemplo implementa um elemento de associação de segurança de descoberta que cria canais seguros. Os canais de segurança se aplicam e verifique se as assinaturas de mensagem são aplicados no topo da pilha atual.  
  
 O elemento de ligação seguro compila as fábricas de canal seguro e ouvintes de canais.  
  
## <a name="secure-channel-factory"></a>Fábrica de canais seguros  
 A fábrica de canais seguros cria saída ou canais duplex que adicionar uma assinatura compact para cabeçalhos de mensagem. Para manter as mensagens tão pequena quanto possível o formato de assinatura compact é usado. A estrutura de uma assinatura compact é mostrada no exemplo a seguir.  
  
```xml  
<d:Security ... >   
  [<d:Sig Scheme="xs:anyURI"   
         [KeyId="xs:base64Binary"]?  
          Refs="..."  
         [PrefixList]="xs:NMTOKENS"   
          Sig="xs:base64Binary"   
          ... />]?  
  ...   
</d:Security>  
```  
  
> [!NOTE]
>  O `PrefixList` foi adicionado no protocolo de versão de descoberta de 2008.  
  
 Para calcular a assinatura, o exemplo determina os itens de assinatura expandida. Uma assinatura XML (`SignedInfo`) é criado usando o `ds` prefixo de namespace, conforme exigido pela especificação WS-Discovery. O corpo e todos os cabeçalhos de descoberta e a resolução de namespaces são referenciados na assinatura, para que eles não possam ser violados. Cada elemento referenciado é transformado usando a canonicalização exclusivo (http://www.w3.org/2001/10/xml-exc-c14n# ), e, em seguida, um valor de digest SHA-1 é computado (http://www.w3.org/2000/09/xmldsig#sha1 ). Com base em todos os elementos e seus valores de resumo, o valor de assinatura é calculado usando o algoritmo RSA (http://www.w3.org/2000/09/xmldsig#rsa-sha1 ).  
  
 As mensagens são assinadas com um certificado de cliente especificado. O local do repositório, o nome e o nome de assunto do certificado devem ser especificados quando o elemento de associação é criado. O `KeyId` na assinatura compact representa o identificador de chave de token de assinatura e é o assunto chave identificador SKI () do token de assinatura ou (se o SKI não existir) um hash SHA-1 da chave pública do token de assinatura.  
  
## <a name="secure-channel-listener"></a>Ouvinte de canal seguro  
 O ouvinte de canais seguros cria canais de entrada ou duplex que verificam a assinatura compact nas mensagens recebidas. Para verificar a assinatura, o `KeyId` especificado na compactar anexada à mensagem de assinatura é usada para selecionar um certificado do repositório especificado. Se a mensagem não tem uma assinatura ou a verificação de assinatura falhar, as mensagens são descartadas. Para usar a associação de segurança, o exemplo define uma fábrica que cria personalizada <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> e <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> com o elemento de associação de segurança de descoberta adicionado. Esses pontos de extremidade seguros podem ser usados em ouvintes de comunicado de descoberta e serviços podem ser descobertos.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 O exemplo inclui uma biblioteca e 4 aplicativos de console:  
  
- **DiscoverySecurityChannels**: Uma biblioteca que expõe a associação de segurança. A biblioteca computa e verifica a assinatura compact para mensagens de entrada/saída.  
  
- **Serviço**: Um serviço que expõe o contrato ICalculatorService, auto-hospedado. O serviço está marcado como detectável. O usuário Especifica os detalhes do certificado usado para assinar as mensagens, especificando o local do repositório e o nome e o nome da entidade ou outro identificador exclusivo para o certificado e o armazenamento onde os certificados de cliente estão localizados (os certificados usados para verificar a assinatura para mensagens de entrada). Com base nesses detalhes, um UdpDiscoveryEndpoint com segurança adicional é criado e usado.  
  
- **Cliente**: Esta classe tenta descobrir um ICalculatorService e para chamar métodos no serviço. Novamente, um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> com adicionado a segurança é criada e usada para assinar e verificar as mensagens.  
  
- **AnnouncementListener**: Um serviço auto-hospedado que escuta anúncios online e offline e usa o ponto de extremidade de comunicado de seguro.  
  
> [!NOTE]
>  Se o Setup. bat for executado várias vezes, o Gerenciador de certificados solicitará a escolha de um certificado para adicionar, pois há certificados duplicados. Nesse caso, o Setup. bat deve ser anulada e Cleanup deve ser chamado, porque as duplicatas já foram criadas. CleanUp também solicitará que você escolha um certificado a ser excluído. Selecione um certificado na lista e continuar a executar CleanUp até que nenhum certificado restantes.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1. Execute o script de Setup. bat de um Prompt de comando do desenvolvedor para Visual Studio. O exemplo usa certificados para assinar e verificar as mensagens. O script cria os certificados usando Makecert.exe e, em seguida, instala-os usando Certmgr.exe. O script deve ser executado com privilégios de administrador.  
  
2. Para compilar e executar o exemplo, abra o arquivo Security.sln no Visual Studio e escolha **Rebuild All**. Atualizar as propriedades de solução para iniciar projetos múltiplos: selecione **iniciar** para todos os projetos, exceto DiscoverySecureChannels. Execute a solução normalmente.  
  
3. Depois de terminar com o exemplo, execute o script de CleanUp que remove os certificados criados para este exemplo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DiscoveryScenario`  
