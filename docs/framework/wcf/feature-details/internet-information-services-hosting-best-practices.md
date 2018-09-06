---
title: Práticas recomendadas de hospedagem dos Serviços de Informações da Internet
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: 0ca5e20b846a1b10f5a52748ff06a4af958b2f4c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865901"
---
# <a name="internet-information-services-hosting-best-practices"></a>Práticas recomendadas de hospedagem dos Serviços de Informações da Internet
Este tópico descreve algumas práticas recomendadas para a hospedagem de serviços Windows Communication Foundation (WCF).  
  
## <a name="implementing-wcf-services-as-dlls"></a>A implementação de serviços do WCF como DLLs  
 Implementando um WCF serviço como uma DLL que é implantado para o diretório \bin de um aplicativo Web que permite que reutilizar o serviço de fora do modelo de aplicativo Web, por exemplo, em um ambiente de teste que pode não ter o Internet Information Services (IIS) implantado.  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>Hosts de serviço em aplicativos hospedados no IIS  
 Não use as APIs de hospedagem interna fundamentais para criar novos hosts de serviço que escutam em transportes de rede não compatível nativamente com o ambiente de hospedagem do IIS (por exemplo, [!INCLUDE[iis601](../../../../includes/iis601-md.md)] para TCP de hospedar serviços, porque a comunicação TCP não tem suporte nativo no [!INCLUDE[iis601](../../../../includes/iis601-md.md)]). Essa abordagem não é recomendada. Hosts de serviço criadas imperativamente não são conhecidos no ambiente de hospedagem do IIS. O ponto crítico é que processamento feito pelo serviços imperativamente criado não é considerado pelo IIS quando ele determina se o pool de aplicativos de hospedagem está ocioso. O resultado é que os aplicativos que têm esses hosts de serviço imperativamente criado tem um ambiente de hospedagem IIS agressivamente descarta os processos de host do IIS.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>URIs e pontos de extremidade hospedado no IIS  
 Pontos de extremidade para um serviço hospedado no IIS devem ser configurados usando relativo recurso uniformes (URIs), endereços absolutos não. Isso garante que o endereço do ponto de extremidade fica dentro do conjunto de endereços de URI que pertencem ao aplicativo de hospedagem e garante que a ativação baseada em mensagem ocorra conforme o esperado.  
  
## <a name="state-management-and-process-recycling"></a>Gerenciamento de estado e a reciclagem de processo  
 O ambiente de hospedagem do IIS é otimizado para serviços que não mantêm o estado local na memória. O IIS recicla o processo de host em resposta a uma variedade de eventos internos e externos, fazendo com que qualquer estado volátil armazenado exclusivamente na memória serão perdidos. Serviços hospedados no IIS deve armazenar seu estado externo ao processo (por exemplo, em um banco de dados) ou em um cache na memória que pode ser facilmente recriado se um aplicativo reciclar o evento ocorre.  
  
> [!NOTE]
>  Os protocolos que usam o WCF para segurança e confiabilidade de camada de mensagem fizer usam do estado na memória volátil. Sessões confiáveis do WCF e sessões de segurança podem encerrar inesperadamente devido a reciclagens do aplicativo. Aplicativos hospedados no IIS que usam um desses protocolos qualquer uma depende de algo que não seja a chave de sessão fornecido pelo WCF para correlacionar o estado da camada de aplicativo (por exemplo, uma construção de camada de aplicativo ou um cabeçalho de correlação personalizada) ou desabilitar Processo do IIS de reciclagem para o aplicativo hospedado.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Otimizando o desempenho em cenários de camada intermediária  
 Para otimizar o desempenho em um *cenário de camada intermediária*— um serviço que chama outros serviços em resposta às mensagens de entrada — instanciar o cliente do serviço WCF ao serviço remoto uma vez e reutilizá-lo em vários entrada solicitações. Criando uma instância de clientes de serviço do WCF é uma operação cara em relação ao que fazer com que um serviço de chamada em uma instância do cliente já existente e cenários de camada intermediária produzem ganhos de desempenho distintos armazenando em cache a clientes remotos em todas as solicitações. Clientes de serviço do WCF são thread-safe, portanto, não é necessário sincronizar o acesso a um cliente entre vários threads.  
  
 Cenários de camada intermediária também produzem ganhos de desempenho usando as APIs assíncronas geradas pelo `svcutil /a` opção. O `/a` opção faz com que o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar `BeginXXX/EndXXX` métodos para cada operação de serviço, que permite chamadas de execução potencialmente longa para serviços remotos a ser feita no threads em segundo plano.  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>WCF em cenários de hospedagem múltipla ou múltipla nomeados  
 Você pode implantar os serviços WCF dentro de um farm da Web do IIS, onde um conjunto de computadores compartilham o nome comum externo (como http://www.contoso.com) mas individualmente são endereçadas por nomes de host diferentes (por exemplo, http://www.contoso.com pode direcionar o tráfego para dois computadores diferentes chamado http://machine1.internal.contoso.com e http://machine2.internal.contoso.com). Neste cenário de implantação é totalmente suportado pelo WCF, mas requer configuração especial do site da Web do IIS que hospeda serviços WCF para exibir o nome de host correto (externo) nos metadados do serviço (Web Services Description Language).  
  
 Para garantir que o nome de host correto apareça nos metadados de serviço WCF gera, configurar a identidade padrão para o site da Web do IIS que hospeda os serviços do WCF para usar um nome de host explícito. Por exemplo, os computadores que residem no interior do farm www.contoso.com devem usar uma associação de site do IIS de *:80:www.contoso.com para HTTP e \*: 443:www.contoso.com para HTTPS.  
  
 Você pode configurar as ligações do site da Web do IIS usando o snap-in do Console de gerenciamento Microsoft (MMC) do IIS.  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Assemblies de outras contas na pasta temporária de substituir os Pools de aplicativos em execução em contextos de usuário diferente  
 Para garantir que os pools de aplicativos em execução em contextos de usuário diferente não é possível substituir os assemblies de outras contas em temporárias [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] arquivos de pasta, use diferentes identidades e as pastas temporárias para diferentes aplicativos. Por exemplo, se você tiver dois /Application1 de aplicativos virtuais e / Application2, você pode criar dois pools de aplicativos, A e B, com duas identidades diferentes. Um pool de aplicativos pode executar a identidade de usuário em uma (user1) enquanto o pool de aplicativos B pode ser executado em outra identidade de usuário (user2) e configurar /Application1 para uso A e /Application2 usar B.  
  
 No Web. config, você pode configurar a pasta temporária usando \< system.web/compilation/@tempFolder>. Para /Application1, pode ser "c:\tempForUser1" e "c:\tempForUser2" pode ser para application2. Conceda permissão de gravação correspondente a essas pastas para as duas identidades.  
  
 Em seguida, Usuário2 não é possível alterar a pasta de geração de código para /application2 (em c:\tempForUser1).  
  
## <a name="enabling-asynchronous-processing"></a>Habilitando o processamento assíncrono  
 Por padrão, as mensagens enviadas para um serviço WCF hospedado no IIS 6.0 e versões anteriores são processadas de forma síncrona. O ASP.NET chama ao WCF em seu próprio thread (o thread de trabalho do ASP.NET) e o WCF usa outro thread para processar a solicitação. WCF mantiver o thread de trabalho do ASP.NET até concluir seu processamento. Isso leva ao processamento assíncrono de solicitações. Processamento de solicitações de forma assíncrona permite maior escalabilidade porque reduz o número de threads necessários para processar uma solicitação – WCF não mantém para o thread do ASP.NET ao processar a solicitação. Uso do comportamento assíncrono não é recomendado para computadores executando o IIS 6.0 porque não há nenhuma maneira de limitar as solicitações de entrada que abra o servidor *negação de serviço* ataques (DOS). Começando com o IIS 7.0, uma limitação de solicitações simultâneas foi introduzida: `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`. Com essa nova limitação é seguro usar o processamento assíncrono.  Por padrão no IIS 7.0, o manipulador assíncrono e o módulo são registrados. Se isso tiver sido desativado, você pode habilitar manualmente o processamento assíncrono de solicitações no arquivo de Web. config do seu aplicativo. As configurações que você usa dependem sua `aspNetCompatibilityEnabled` configuração. Se você tiver `aspNetCompatibilityEnabled` definido como `false`, configure o `System.ServiceModel.Activation.ServiceHttpModule` conforme mostrado no seguinte trecho de configuração.  
  
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
  
 Se você tiver `aspNetCompatibilityEnabled` definido como `true`, configure o `System.ServiceModel.Activation.ServiceHttpHandlerFactory` conforme mostrado no seguinte trecho de config.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Exemplos do serviço de hospedagem](https://msdn.microsoft.com/library/f703a3f6-0fba-418a-a92f-7ce75ccfa47e)  
 [Recursos de hospedagem do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
