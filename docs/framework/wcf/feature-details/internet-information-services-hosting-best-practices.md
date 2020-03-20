---
title: Práticas recomendadas de hospedagem dos Serviços de Informações da Internet
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: 3be9d4c81f891ad898099ba9041a09b16388b7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184717"
---
# <a name="internet-information-services-hosting-best-practices"></a>Práticas recomendadas de hospedagem dos Serviços de Informações da Internet
Este tópico descreve algumas práticas recomendadas para hospedar serviços da Windows Communication Foundation (WCF).  
  
## <a name="implementing-wcf-services-as-dlls"></a>Implementação de Serviços WCF como DLLs  
 A implementação de um serviço WCF como dLL que é implantado no diretório \bin de um aplicativo da Web permite que você reutilize o serviço fora do modelo de aplicativo da Web, por exemplo, em um ambiente de teste que pode não ter o IIS (Internet Information Services, serviços de informação da Internet) implantado.  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>Hosts de serviço em aplicativos hospedados no IIS  
 Não use as APIs de auto-host imperativas para criar novos hosts de serviço que ouçam transportes de rede não suportados nativamente pelo ambiente de hospedagem Do IIS (Por exemplo, O IIS 6.0 para hospedar serviços TCP, porque a comunicação TCP não é suportada nativamente no IIS 6.0). Essa abordagem não é recomendada. Os hosts de serviço criados imperativamente não são conhecidos dentro do ambiente de hospedagem do IIS. O ponto crítico é que o processamento feito por serviços criados de forma imperativamente não é contabilizado pelo IIS quando determina se o pool de aplicativos de hospedagem está ocioso. O resultado é que os aplicativos que têm hosts de serviço tão imperativamente criados têm um ambiente de hospedagem IIS que elimina agressivamente os processos de host do IIS.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>Pontos finais hospedados em URIs e IIS  
 Os pontos finais de um serviço hospedado no IIS devem ser configurados usando URIs (Uniform Resource Identifiers, identificadores de recursos uniformes) relativos, não endereços absolutos. Isso garante que o endereço de ponto final se recai sobre o conjunto de endereços URI que pertencem ao aplicativo de hospedagem e garante que a ativação baseada em mensagens aconteça como esperado.  
  
## <a name="state-management-and-process-recycling"></a>Gestão Estadual e Reciclagem de Processos  
 O ambiente de hospedagem do IIS é otimizado para serviços que não mantêm o estado local na memória. O IIS recicla o processo de host em resposta a uma variedade de eventos externos e internos, fazendo com que qualquer estado volátil armazenado exclusivamente na memória seja perdido. Os serviços hospedados no IIS devem armazenar seu estado externo ao processo (por exemplo, em um banco de dados) ou em um cache na memória que pode ser facilmente recriado se ocorrer um evento de reciclagem de aplicativos.  
  
> [!NOTE]
> Os protocolos que o WCF usa para confiabilidade e segurança da camada de mensagem fazem uso do estado volátil na memória. Sessões confiáveis do WCF e sessões de segurança podem terminar inesperadamente devido às reciclagems de aplicativos. Os aplicativos hospedados no IIS que fazem uso desses protocolos devem depender de algo diferente da chave de sessão fornecida pelo WCF para correlacionar o estado da camada de aplicativo (por exemplo, um conjunto de camadas de aplicativo ou cabeçalho de correlação personalizado) ou desativar Reciclagem do processo IIS para a aplicação hospedada.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Otimização do desempenho em cenários intermediários  
 Para obter um desempenho ideal em um *cenário intermediário*— um serviço que chama outros serviços em resposta a mensagens recebidas — instanciar o cliente de serviço WCF ao serviço remoto uma vez e reutilizá-lo em várias solicitações recebidas. A instanciação de clientes de serviços WCF é uma operação cara em relação a fazer uma chamada de serviço em uma instância de cliente pré-existente, e cenários de nível intermediário produzem ganhos de desempenho distintos ao cachear clientes remotos entre as solicitações. Os clientes de serviço WCF são seguros para threads, portanto não é necessário sincronizar o acesso a um cliente em vários segmentos.  
  
 Cenários intermediários também produzem ganhos de desempenho usando as `svcutil /a` APIs assíncronas geradas pela opção. A `/a` opção faz com que a [ServiceModel Metadata Utility Tool (Svcutil.exe) gere](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) `BeginXXX/EndXXX` métodos para cada operação de serviço, o que permite que chamadas potencialmente longas para serviços remotos sejam feitas em threads de fundo.  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>WCF em cenários multi-homed ou multi-nomeados  
 Você pode implantar serviços WCF dentro de uma fazenda Web IIS, onde `http://www.contoso.com`um conjunto de computadores compartilham um nome `http://www.contoso.com` externo comum (como `http://machine1.internal.contoso.com` `http://machine2.internal.contoso.com`) mas são abordados individualmente por diferentes nomes de host (por exemplo, podem direcionar o tráfego para duas máquinas diferentes nomeadas e ). Este cenário de implantação é totalmente suportado pelo WCF, mas requer configuração especial dos serviços WCF de hospedagem do site IIS para exibir o nome de host correto (externo) nos metadados do serviço (Linguagem de Descrição de Serviços da Web).  
  
 Para garantir que o nome de host correto seja exibido no metadados de serviço que o WCF gera, configure a identidade padrão para o site da Web IIS que hospeda serviços WCF para usar um nome de host explícito. Por exemplo, os computadores `www.contoso.com` que residem dentro da fazenda devem usar uma vinculação do \*site IIS de *:80:www.contoso.com para HTTP e :443:www.contoso.com para HTTPS.  
  
 Você pode configurar as vinculações do site do IIS usando o snap-in do IIS Microsoft Management Console (MMC).  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Pools de aplicativos em execução em diferentes contextos de usuário Sobrepor montagens de outras contas na pasta temporária  
 Para garantir que os pools de aplicativos em execução em diferentes contextos de usuário não possam substituir conjuntos de outras contas na pasta de arquivos ASP.NET temporários, usar diferentes identidades e pastas temporárias para diferentes aplicativos. Por exemplo, se você tiver dois aplicativos virtuais /Application1 e / Application2, você pode criar dois pools de aplicativos, A e B, com duas identidades diferentes. O pool de aplicativos A pode ser executado uma identidade de usuário (usuário1) enquanto o pool de aplicativos B pode ser executado outra identidade de usuário (usuário2) e configurar /Application1 para usar A e /Application2 para usar B.  
  
 Na Web.config, você pode configurar \< system.web/compilation/@tempFolder a pasta temporária usando>. Para /Application1, pode ser "c:\tempForUser1" e para o aplicativo2 pode ser "c:\tempForUser2". Conceda permissão de gravação correspondente a essas pastas para as duas identidades.  
  
 Em seguida, o usuário2 não pode alterar a pasta de geração de código para /application2 (em c:\tempForUser1).  
  
## <a name="enabling-asynchronous-processing"></a>Habilitando o processamento assíncrono  
 Por mensagens padrão enviadas para um serviço WCF hospedado no IIS 6.0 e anteriormente são processadas de forma síncrona. ASP.NET chamadas para wcf em seu próprio segmento (o ASP.NET segmento de trabalhador) e WCF usa outro segmento para processar a solicitação. O WCF mantém o fio ASP.NET trabalhador até que ele complete seu processamento. Isso leva ao processamento síncrono das solicitações. O processamento de solicitações assíncronamente permite maior escalabilidade porque reduz o número de threads necessários para processar uma solicitação – o WCF não se mantém no segmento ASP.NET durante o processamento da solicitação. O uso de comportamento assíncrono não é recomendado para máquinas que executam o IIS 6.0 porque não há como acelerar as solicitações recebidas que abrem o servidor para ataques *de Negação de Serviço* (DOS). A partir do IIS 7.0, foi introduzido `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`um acelerador de solicitação simultâneo: . Com este novo acelerador é seguro usar o processamento assíncrono.  Por padrão no IIS 7.0, o manipulador assíncrono e o módulo são registrados. Se isso tiver sido desligado, você pode ativar manualmente o processamento assíncrono de solicitações no arquivo Web.config do seu aplicativo. As configurações que você `aspNetCompatibilityEnabled` usa dependem da sua configuração. Se você `aspNetCompatibilityEnabled` tiver `false`definido para, configure o `System.ServiceModel.Activation.ServiceHttpModule` como mostrado no trecho de configuração a seguir.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="false" />
  </system.serviceModel>  
  <system.webServer>  
    <modules>  
      <remove name="ServiceModel"/>  
      <add name="ServiceModel"
           preCondition="integratedMode,runtimeVersionv2.0"
           type="System.ServiceModel.Activation.ServiceHttpModule, System.ServiceModel,Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
    </modules>  
    </system.webServer>  
```  
  
 Se você `aspNetCompatibilityEnabled` tiver `true`definido para `System.ServiceModel.Activation.ServiceHttpHandlerFactory` , configure o como mostrado no trecho de configuração a seguir.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
  </system.serviceModel>  
  <system.webServer>  
    <handlers>  
          <clear/>  
          <add name="TestAsyncHttpHandler"
               path="*.svc"
               verb="*"
               type="System.ServiceModel.Activation.ServiceHttpHandlerFactory, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
               />  
    </handlers>
  </system.webServer>  
```  
  
## <a name="see-also"></a>Confira também

- [Amostras de hospedagem de serviços](../samples/hosting.md)
- [Recursos de hospedagem do Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
