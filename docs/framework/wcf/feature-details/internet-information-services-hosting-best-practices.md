---
title: "Práticas recomendadas de hospedagem dos Serviços de Informações da Internet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 60d703336aeac3471e4b554f65998621b5cc8ef8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="internet-information-services-hosting-best-practices"></a>Práticas recomendadas de hospedagem dos Serviços de Informações da Internet
Este tópico descreve algumas práticas recomendadas para hospedagem [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviços.  
  
## <a name="implementing-wcf-services-as-dlls"></a>A implementação de serviços do WCF como DLLs  
 Implementando um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de serviço como uma DLL que é implantada no diretório \bin de um aplicativo Web que permite reutilizar o serviço de fora do modelo de aplicativo da Web, por exemplo, em um ambiente de teste que não pode ter o Internet Information Services (IIS) implantado.  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>Hosts de serviço em aplicativos hospedados no IIS  
 Não use as APIs de hospedagem interna essencial para criar novos hosts de serviço que escutam em transportes de rede sem suporte original pelo ambiente de hospedagem do IIS (por exemplo, [!INCLUDE[iis601](../../../../includes/iis601-md.md)] hospedar o TCP de serviços, como a comunicação TCP de forma nativa não tem suporte no [!INCLUDE[iis601](../../../../includes/iis601-md.md)]). Essa abordagem não é recomendada. Hosts de serviço criada imperativa não são conhecidos no ambiente de hospedagem do IIS. O ponto de crítico é que processamento executado pelos serviços imperativa criados não é considerado pelo IIS quando ele determina se o pool de aplicativos de hospedagem está ocioso. O resultado é que aplicativos que têm esses hosts de serviço imperativa criado tem um ambiente de hospedagem de IIS agressivamente descarta os processos de host IIS.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>URIs e pontos de extremidade hospedado no IIS  
 Pontos de extremidade para um serviço hospedado no IIS devem ser configurados usando relativo URIs Uniform Resource Identifier (), endereços não é absolutos. Isso garante que o endereço do ponto de extremidade fica dentro do conjunto de endereços URI que pertencem ao aplicativo de hospedagem e garante que a ativação baseada em mensagem ocorre como esperado.  
  
## <a name="state-management-and-process-recycling"></a>Gerenciamento de estado e a reciclagem de processo  
 O ambiente de hospedagem do IIS é otimizado para serviços que não mantêm o estado local na memória. IIS recicla o processo de host em resposta a uma variedade de eventos internos e externos, fazendo com que qualquer estado volátil armazenado exclusivamente na memória serão perdidos. Serviços hospedados no IIS deve armazenar seu estado externo para o processo (por exemplo, em um banco de dados) ou em um cache na memória que pode ser facilmente recriado se um aplicativo reciclar o evento ocorre.  
  
> [!NOTE]
>  Os protocolos [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fazer usa para segurança e confiabilidade de camada de mensagem usar o estado de memória voláteis. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]sessões confiáveis e sessões de segurança podem encerrar inesperadamente devido a reciclagem do aplicativo. Aplicativos hospedados no IIS que usam os protocolos o depende de algo diferente do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-fornecido a chave de sessão para correlacionar o estado da camada de aplicativo (por exemplo, uma construção de camada de aplicativo ou um cabeçalho de correlação personalizado) ou desabilitar reciclagem para o aplicativo hospedado de processo do IIS.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Otimizando o desempenho em cenários de camada intermediária  
 Para otimizar o desempenho em um *cenário de camada intermediária*— um serviço que chama outros serviços em resposta a mensagens de entrada — instanciar o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço cliente para o serviço remoto uma vez e reutilizá-la em vários solicitações de entrada. Criando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clientes de serviço é uma operação cara relativo ao fazer com que um serviço de chamada em uma instância do cliente já existente e cenários de camada intermediária produzem ganhos de desempenho distintos armazenando em cache a clientes remotos em solicitações. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]clientes de serviço são thread-safe, portanto, não é necessário sincronizar o acesso a um cliente em vários threads.  
  
 Cenários de camada intermediária também produzem ganhos de desempenho usando as APIs assíncronas geradas pelo `svcutil /a` opção. O `/a` opção faz com que o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar `BeginXXX/EndXXX` métodos para cada operação de serviço, que permite que chamadas potencialmente de longa execução serviços remotos a serem feitas no threads em segundo plano.  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>WCF em cenários de hospedagem múltipla ou várias nomeados  
 Você pode implantar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços dentro de um farm da Web do IIS, onde um conjunto de computadores compartilham um externo comuns nome (por exemplo, http://www.contoso.com), mas individualmente são endereçados por nomes de host diferentes (por exemplo, http://www.contoso.com pode direcionar o tráfego para duas máquinas diferentes chamados http://machine1.internal.contoso.com e http://machine2.internal.contoso.com). Neste cenário de implantação tem suporte completo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], mas requer configuração especial do site da Web do IIS que hospeda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços para exibir o nome do host (externo) correta nos metadados do serviço (Web Services Description Language).  
  
 Para garantir que o nome de host correto é exibido nos metadados do serviço [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera, configurar a identidade padrão para o site da Web do IIS que hospeda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services para usar um nome de host explícito. Por exemplo, os computadores que residem dentro do farm www.contoso.com devem usar uma associação de site do IIS de *:80:www.contoso.com para HTTP e \*: 443:www.contoso.com para HTTPS.  
  
 Você pode configurar as ligações de site da Web do IIS usando o snap-in do Console de gerenciamento Microsoft (MMC) do IIS.  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Pools de aplicativos em execução em contextos de usuário diferente Substituir Assemblies de outras contas na pasta temporária  
 Para garantir que os pools de aplicativos em execução em contextos de usuário diferente não é possível substituir os assemblies de outras contas em temporárias [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] arquivos de pasta, use diferentes identidades e pastas temporárias para diferentes aplicativos. Por exemplo, se você tiver dois /Application1 de aplicativos virtuais e / Application2, você pode criar dois pools de aplicativos, A e B, com duas identidades diferentes. Um pool de aplicativos pode executar a identidade de usuário em um único (Usuário1) enquanto o pool de aplicativo B pode ser executado em outra identidade de usuário (Usuário2) e configurar /Application1 para um uso e /Application2 usar B.  
  
 No Web. config, você pode configurar a pasta temporária usando \< system.web/compilation/@tempFolder>. Para /Application1, ele pode ser "c:\tempForUser1" e para application2 pode ser "c:\tempForUser2". Conceda permissão de gravação correspondente a essas pastas para duas identidades.  
  
 Em seguida, o Usuário2 não é possível alterar a pasta de geração de código para /application2 (em c:\tempForUser1).  
  
## <a name="enabling-asynchronous-processing"></a>Habilitando o processamento assíncrono  
 Por padrão mensagens enviadas para um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço hospedado no IIS 6.0 e versões anteriores são processados de maneira síncrona. ASP.NET chama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em seu próprio thread (o thread de trabalho do ASP.NET) e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa outro thread para processar a solicitação. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]o thread de trabalho do ASP.NET mantiver até concluir seu processamento. Isso resulta em processamento síncrono de solicitações. Processamento de solicitações de forma assíncrona permite maior escalabilidade porque reduz o número de threads necessários para processar uma solicitação –[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não manter o thread do ASP.NET ao processar a solicitação. Uso de comportamento assíncrono não é recomendado para computadores que executam o IIS 6.0 porque não há nenhuma maneira de controlar solicitações de entrada que abra o servidor *negação de serviço* ataques. Começando com o IIS 7.0, uma limitação de solicitações simultâneas foi introduzida: `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`. Com essa nova limitação é seguro usar o processamento assíncrono.  Por padrão no IIS 7.0, o manipulador assíncrono e o módulo são registrados. Se isso tiver sido desativado, você pode habilitar manualmente o processamento assíncrono de solicitações no arquivo Web. config de seu aplicativo. As configurações que você usa dependem seu `aspNetCompatibilityEnabled` configuração. Se você tiver `aspNetCompatibilityEnabled` definida como `false`, configure o `System.ServiceModel.Activation.ServiceHttpModule` conforme mostrado no seguinte trecho de configuração.  
  
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
  
 Se você tiver `aspNetCompatibilityEnabled` definida como `true`, configure o `System.ServiceModel.Activation.ServiceHttpHandlerFactory` conforme mostrado no seguinte trecho de configuração.  
  
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
 [Exemplos do serviço de hospedagem](http://msdn.microsoft.com/en-us/f703a3f6-0fba-418a-a92f-7ce75ccfa47e)  
 [Recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
