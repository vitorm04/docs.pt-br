---
title: Exemplo de segurança de descoberta
ms.date: 03/30/2017
ms.assetid: b8db01f4-b4a1-43fe-8e31-26d4e9304a65
ms.openlocfilehash: 00f81d1879d9157a7ecdfa0db8d2ea0d505ad5b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183738"
---
# <a name="discovery-security-sample"></a>Exemplo de segurança de descoberta

A especificação Do Discovery não exige que os pontos finais que participam do processo de descoberta sejam seguros. O aprimoramento das mensagens de descoberta com segurança mitiga vários tipos de ataques (alteração de mensagem, negação de serviço, replay, spoofing). Esta amostra implementa canais personalizados que computam e verificam assinaturas de mensagens usando o formato de assinatura compacta (descrito na Seção 8.2 da especificação WS-Discovery). A amostra suporta tanto a [especificação Discovery de 2005](http://specs.xmlsoap.org/ws/2005/04/discovery/ws-discovery.pdf) quanto a [versão 1.1](http://docs.oasis-open.org/ws-dd/discovery/1.1/cs-01/wsdd-discovery-1.1-spec-cs-01.pdf).  
  
 O canal personalizado é aplicado no topo da pilha de canais existente para pontos finais de Discovery e Announcement. Dessa forma, um cabeçalho de assinatura é aplicado para cada mensagem enviada. A assinatura é verificada nas mensagens recebidas e quando não corresponde ou quando as mensagens não têm uma assinatura, as mensagens são retiradas. Para assinar e verificar mensagens, a amostra usa certificados.  
  
## <a name="discussion"></a>Discussão  
 O WCF é muito extensível e permite aos usuários a possibilidade de personalizar canais conforme desejado. A amostra implementa um elemento de ligação segura de descoberta que constrói canais seguros. Os canais seguros aplicam e verificam assinaturas de mensagens e são aplicados no topo da pilha atual.  
  
 O elemento de ligação segura constrói fábricas de canais seguros e ouvintes de canais.  
  
## <a name="secure-channel-factory"></a>Fábrica de canais seguros  
 A fábrica de canais seguros cria canais de saída ou duplex que adicionam uma assinatura compacta aos cabeçalhos de mensagem. Para manter as mensagens tão pequenas quanto possível, o formato de assinatura compacta é usado. A estrutura de uma assinatura compacta é mostrada no exemplo a seguir.  
  
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
> O `PrefixList` foi adicionado no protocolo de versão discovery de 2008.  
  
 Para calcular a assinatura, a amostra determina os itens de assinatura expandida. Uma assinatura XML (`SignedInfo`) é `ds` criada, usando o prefixo namespace, conforme exigido pela especificação WS-Discovery. O corpo e todos os cabeçalhos na descoberta e endereçamento de namespaces são referenciados na assinatura, de modo que eles não podem ser adulterados. Cada elemento referenciado é transformado usando ahttp://www.w3.org/2001/10/xml-exc-c14n# Canonização Exclusiva ( ), e, emhttp://www.w3.org/2000/09/xmldsig#sha1 seguida, um valor de digestão SHA-1 é calculado ( ). Com base em todos os elementos referenciados e seus valores dehttp://www.w3.org/2000/09/xmldsig#rsa-sha1 digestão, o valor de assinatura é calculado usando o algoritmo RSA ( ).  
  
 As mensagens são assinadas com um certificado especificado pelo cliente. O local da loja, o nome e o nome do assunto do certificado devem ser especificados quando o elemento de vinculação for criado. A `KeyId` assinatura compacta representa o identificador-chave do token de assinatura e é o Identificador de Tecla de Assunto (SKI) do token de assinatura ou (se o SKI não existir) um hash SHA-1 da chave pública do token de assinatura.  
  
## <a name="secure-channel-listener"></a>Ouvinte de canal seguro  
 O ouvinte de canal seguro cria canais de entrada ou duplex que verificam a assinatura compacta nas mensagens recebidas. Para verificar a `KeyId` assinatura, a especificada na assinatura compacta anexada à mensagem é usada para selecionar um certificado na loja especificada. Se a mensagem não tiver uma assinatura ou a verificação de assinatura falhar, as mensagens serão retiradas. Para usar a vinculação segura, a amostra <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> define uma fábrica que cria um elemento de ligação segura de descoberta adicionado. Esses pontos finais seguros podem ser usados em ouvintes de anúncios de descobertas e serviços de descoberta.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 A amostra inclui uma biblioteca e 4 aplicativos de console:  
  
- **DiscoverySecurityChannels**: Uma biblioteca que expõe a vinculação segura. A biblioteca calcula e verifica a assinatura compacta para mensagens de saída/entrada.  
  
- **Serviço**: Um serviço que exponha o contrato iCalculatorService, auto-hospedado. O serviço é marcado como Discoverable. O usuário especifica os detalhes do certificado usado para assinar mensagens especificando o local e o nome da loja e o nome do assunto ou outro identificador exclusivo para o certificado, e a loja onde os certificados do cliente estão localizados (os certificados usados para verificar a assinatura das mensagens recebidas). Com base nesses detalhes, um UdpDiscoveryEndpoint com segurança adicional é construído e usado.  
  
- **Cliente**: Esta classe tenta descobrir um ICalculatorService e chamar métodos no serviço. Novamente, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> um com segurança adicional é construído e usado para assinar e verificar as mensagens.  
  
- **AnnouncementListener**: Um serviço auto-hospedado que ouve anúncios on-line e off-line e usa o ponto final do anúncio seguro.  
  
> [!NOTE]
> Se o Setup.bat for executado várias vezes, o gerenciador de certificados solicita que você escolha um certificado para adicionar, pois há certificados duplicados. Nesse caso, setup.bat deve ser abortado e Cleanup.bat deve ser chamado, porque as duplicatas já foram criadas. Cleanup.bat também solicita que você escolha um certificado para excluir. Selecione um certificado na lista e continue executando Cleanup.bat até que não restem certificados.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1. Execute o script Setup.bat a partir de um prompt de comando de desenvolvedor para o Visual Studio. A amostra usa certificados para assinar e verificar mensagens. O script cria os certificados usando Makecert.exe e, em seguida, instala-os usando Certmgr.exe. O script deve ser executado com privilégios de administrador.  
  
2. Para construir e executar a amostra, abra o arquivo Security.sln no Visual Studio e escolha **Reconstruir tudo**. Atualize as propriedades da solução para iniciar vários projetos: selecione **Iniciar** para todos os projetos, exceto DiscoverySecureChannels. Execute a solução normalmente.  
  
3. Depois de terminar com a amostra, execute o script Cleanup.bat que remove os certificados criados para esta amostra.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DiscoveryScenario`  
