---
title: "Exemplo de segurança de descoberta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8db01f4-b4a1-43fe-8e31-26d4e9304a65
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 2b21017be0927f0d5189744111437c5afa6dd623
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="discovery-security-sample"></a>Exemplo de segurança de descoberta
A especificação de descoberta não requer que os pontos de extremidade que participam do processo de descoberta para ser seguro. Aprimorando as mensagens de descoberta com segurança reduz os vários tipos de ataques (negação de serviço, a alteração da mensagem, reproduzir, falsificação). Este exemplo implementa canais personalizados de computação e verificar as assinaturas de mensagem usando o formato de assinatura compact (descrito na seção 8.2 da especificação WS-Discovery). O exemplo dá suporte ao [especificação de descoberta de 2005](http://go.microsoft.com/fwlink/?LinkId=177912) e [versão 1.1](http://go.microsoft.com/fwlink/?LinkId=179677).  
  
 O canal personalizado é aplicado na parte superior da pilha de canais existentes para pontos de extremidade de descoberta e o anúncio. Dessa forma, um cabeçalho de assinatura é aplicado a todas as mensagens enviadas. A assinatura é verificada nas mensagens recebidas e quando ela não corresponde, ou quando as mensagens não tem uma assinatura, as mensagens serão descartadas. Para assinar e verificar as mensagens, o exemplo usa certificados.  
  
## <a name="discussion"></a>Discussão  
 O WCF é muito extensível e permite que os usuários a possibilidade de personalizar canais conforme desejado. O exemplo implementa um elemento de associação de segurança de descoberta que cria canais seguros. Os canais de segurança se aplicam e verificar as assinaturas de mensagem em são aplicados no topo da pilha atual.  
  
 O elemento de associação de segurança cria fábricas de canal seguro e ouvintes de canais.  
  
## <a name="secure-channel-factory"></a>Fábrica de canal seguro  
 A fábrica de canal seguro cria saída ou canais duplex de adicionar uma assinatura compact para cabeçalhos de mensagem. Para manter as mensagens tão pequenas quanto possível o formato de assinatura compact é usado. A estrutura de uma assinatura do compact é mostrada no exemplo a seguir.  
  
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
>  O `PrefixList` foi adicionado o protocolo de versão de descoberta de 2008.  
  
 Para calcular a assinatura, o exemplo determina os itens de assinatura expandida. Uma assinatura XML (`SignedInfo`) é criado usando o `ds` prefixo de namespace, conforme exigido pela especificação WS-Discovery. O corpo e todos os cabeçalhos de descoberta e a resolução namespaces são referenciados na assinatura, portanto não pode ser violados. Cada elemento referenciado é transformado usando canonização do exclusivo (http://www.w3.org/2001/10/xml-exc-c14n#) e, em seguida, um valor de resumo de SHA-1 é computada (http://www.w3.org/2000/09/xmldsig#sha1). Com base em todos os elementos e seus valores de resumo, o valor de assinatura é calculado usando o algoritmo RSA (http://www.w3.org/2000/09/xmldsig#rsa-sha1).  
  
 As mensagens são assinadas com um certificado de cliente especificado. O local de armazenamento, o nome e o nome de assunto do certificado devem ser especificados quando o elemento de associação é criado. O `KeyId` na assinatura compact representa o identificador de chave de token de assinatura e é o assunto chave identificador SKI () do token de autenticação ou (se não existir o SKI) um hash SHA-1 da chave pública do token de assinatura.  
  
## <a name="secure-channel-listener"></a>Ouvinte de canal seguro  
 O ouvinte de canal seguro cria canais de entrada ou duplex que verificam a assinatura compact em mensagens recebidas. Para verificar a assinatura, o `KeyId` especificado no compact anexada à mensagem de assinatura é usada para selecionar um certificado do armazenamento especificado. Se a mensagem não tem uma assinatura ou a verificação de assinatura falhar, as mensagens são descartadas. Para usar a associação de segurança, o exemplo define uma fábrica que cria personalizada <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> e <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> com o elemento de associação de segurança de descoberta adicional. Esses pontos de extremidade seguros podem ser usados nos serviços detectáveis e ouvintes de anúncio de descoberta.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 O exemplo inclui uma biblioteca e 4 aplicativos de console:  
  
-   **DiscoverySecurityChannels**: uma biblioteca que expõe a associação de segurança. A biblioteca calcula e verifica a assinatura compact para mensagens de entrada/saída.  
  
-   **Serviço**: um serviço expondo ICalculatorService contrato, self-host. O serviço está marcado como detectável. O usuário Especifica os detalhes do certificado usado para assinar mensagens, especificando o local do repositório e o nome e o nome da entidade ou outro identificador exclusivo para o certificado e o armazenamento onde os certificados de cliente estão localizados (os certificados usados para verificar a assinatura para as mensagens de entrada). Com base nesses detalhes, um UdpDiscoveryEndpoint com segurança adicional é criado e usado.  
  
-   **Cliente**: esta classe tenta descobrir um ICalculatorService e para chamar métodos no serviço. Novamente, um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> com adicionado segurança é criada e usada para assinar e verificar as mensagens.  
  
-   **AnnouncementListener**: um serviço auto-hospedado que escuta anúncios online e offline e usa o ponto de extremidade de comunicado de segurança.  
  
> [!NOTE]
>  Se bat será executado várias vezes, o Gerenciador de certificados solicitará para escolher um certificado a ser adicionado, pois há certificados duplicados. Nesse caso, bat deve ser anulada e Cleanup.bat deve ser chamado porque as duplicatas já foram criadas. CleanUp.bat também solicita que você escolha um certificado a ser excluído. Selecione um certificado na lista e continuar a executar Cleanup.bat até que nenhum certificado está pendente.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Execute o script de bat em um prompt de comando do Visual Studio. O exemplo usa certificados para assinar e verificar as mensagens. O script cria os certificados usando Makecert.exe e, em seguida, instala-os usando Certmgr.exe. O script deve ser executado com privilégios de administrador.  
  
2.  Para compilar e executar o exemplo, abra o arquivo Security.sln no Visual Studio e escolha **recriar todos os**. Atualizar as propriedades da solução para iniciar vários projetos: selecione **iniciar** para todos os projetos, exceto DiscoverySecureChannels. Execute a solução normalmente.  
  
3.  Depois que você concluir o exemplo, execute o script de Cleanup.bat que remove os certificados criados para este exemplo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DiscoveryScenario`  
  
## <a name="see-also"></a>Consulte também
