---
title: "Implantando um Serviço WCF hospedado do Internet Information Services dos Serviços de Informações da Internet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
caps.latest.revision: "30"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 42c30c5f83f8245531a357c2d0b179deb87a2845
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Implantando um Serviço WCF hospedado do Internet Information Services dos Serviços de Informações da Internet
Desenvolver e implantar um serviço do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hospedado no IIS (Serviços de Informações da Internet) consiste nas seguintes tarefas:  
  
-   Verificar se o IIS, o ASP.NET, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e o componente de ativação do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] estão instalados e registrados corretamente.  
  
-   Criar um novo aplicativo do IIS ou reutilizar um existente do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
-   Criar um arquivo .svc para o serviço do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   Implantar a implementação do serviço para o aplicativo do IIS.  
  
-   Configurar o serviço do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Para obter uma explicação detalhada de criação de um hospedados no IIS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de serviço, consulte [como: hospedar um serviço WCF no IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>Verificar se o IIS, o ASP.NET, o WCF estão corretamente instalados e registrados  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], o IIS e o ASP.NET devem estar instalados para que os serviços do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hospedados no IIS funcionem corretamente. Os procedimentos para instalar o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (como parte do [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]), o ASP.NET e o IIS variam dependendo da versão do sistema operacional que está sendo usada. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Instalando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], consulte [instalador da Web do Microsoft .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=201185). Instruções para instalar o IIS podem ser encontradas em [instalando o IIS](http://go.microsoft.com/fwlink/?LinkId=201188).  
  
 O processo de instalação para o [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] registra automaticamente o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com o IIS se o IIS já estiver no computador. Se o IIS for instalado após o [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], uma etapa adicional será necessária para registrar o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com o IIS e o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Você pode fazer isso da seguinte maneira, dependendo do sistema operacional:  
  
-   [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)], Windows 7, e [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]: usar o [ferramenta de registro de ServiceModel (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) ferramenta para registrar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com o IIS: para usar essa ferramenta, digite **ServiceModelReg.exe /i /x** em prompt de comando do Visual Studio. Você pode abrir esse comando prompt por clicando no botão Iniciar, selecionando **todos os programas**, **Microsoft Visual Studio 2012**, **ferramentas do Visual Studio**, e  **Prompt de comando do Visual Studio**  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)]: Instalar o subcomponente de componentes de ativação do Windows Communication Foundation do [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]. Para fazer isso, no painel de controle, clique em **adicionar ou remover programas** e **adicionar\/remover componentes do Windows**. Isso ativa a **Assistente de componentes do Windows**.  
  
-   Windows 7:  
  
 Finalmente, você deve verificar se o ASP.NET está configurado para usar a versão 4. do .NET Framework. Faça isso executando a ferramenta ASPNET_Regiis com a opção –i. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Ferramenta de registro ASP.NET IIS](http://go.microsoft.com/fwlink/?LinkId=201186)  
  
## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Criar um novo aplicativo do IIS ou reutilizar um existente do ASP.NET  
 Os serviços do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hospedados no IIS devem residir em um aplicativo do IIS. Você pode criar um novo aplicativo do IIS para hospedar os serviços do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exclusivamente. Como alternativa, você pode implantar um serviço do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em um aplicativo existente que já esteja hospedando o conteúdo do [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] (como páginas .aspx e serviços Web do ASP.NET [ASMX]). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Essas opções, consulte o "hospedagem WCF-lado a lado com o ASP.NET" e "Hospedagem WCF Services no modo de compatibilidade ASP.NET" seções [serviços WCF e ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
 Observe que o [!INCLUDE[iis601](../../../../includes/iis601-md.md)] e as versões posteriores reiniciam periodicamente um aplicativo isolado de programação orientada a objeto. O valor padrão é 1740 minutos. O valor máximo valor com suporte é 71.582 minutos. Esse reinício pode ser desabilitado. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Essa propriedade, consulte o [PeriodicRestartTime](http://go.microsoft.com/fwlink/?LinkId=109968).  
  
## <a name="create-an-svc-file-for-the-wcf-service"></a>Criar um arquivo .svc para o serviço WCF  
 Os serviços do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hospedados no IIS são representados como arquivos de conteúdo especial (arquivos .svc) dentro do aplicativo do IIS. Esse modelo é semelhante à maneira como as páginas ASMX são representadas dentro de um aplicativo do IIS como arquivos .asmx. Um arquivo. svc contém um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-diretiva de processamento específico ([@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)) que permite que o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infraestrutura de hospedagem para ativar serviços hospedados em resposta a mensagens de entrada. A sintaxe mais comum para um arquivo .svc está na instrução a seguir.  
  
```  
<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>  
```  
  
 Ele consiste de [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva e um único atributo, `Service`. O valor do atributo `Service` é o nome do tipo CLR (Common Language Runtime) da implementação do serviço. Usar essa diretiva é basicamente equivalente a criar um host de serviço usando o código a seguir.  
  
```  
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );  
```  
  
 A configuração de hospedagem adicional, como a criação de uma lista de endereços de base para o serviço também pode ser feita. Você também pode usar um <xref:System.ServiceModel.Activation.ServiceHostFactory> personalizado para estender a política para usar com soluções de hospedagem personalizadas. Os aplicativos do IIS que hospedam os serviços do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não são responsáveis por gerenciar a criação e o tempo de vida de instâncias do <xref:System.ServiceModel.ServiceHost>. A infraestrutura de hospedagem do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gerenciado cria dinamicamente a instância necessária do <xref:System.ServiceModel.ServiceHost> quando a primeira solicitação é recebida para o arquivo .svc. A instância não é liberada até que seja fechada explicitamente pelo código ou quando o aplicativo for reciclado.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]a sintaxe para arquivos. svc, consulte [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).  
  
## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Implantar a implementação do serviço para o aplicativo do IIS  
 Os serviços do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hospedados no IIS usam o mesmo modelo de compilação dinâmica que o [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]. Da mesma forma que com o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], você pode implantar o código de implementação para os serviços do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hospedados no IIS de várias maneiras em vários locais, da seguinte maneira:  
  
-   Como um arquivo .dll pré-compilado localizado no GAC (cache de assembly global) ou no diretório \bin do aplicativo. Os binários pré-compilados não são atualizados até que uma nova versão da biblioteca de classe seja implantada.  
  
-   Como arquivos de origem não compilados localizados no diretório \App_Code do aplicativo. Os arquivos de origem localizados nesse diretório são exigidos dinamicamente ao processar a primeira solicitação do aplicativo. As alterações nos arquivos no diretório \App_Code fazem o aplicativo inteiro ser reciclado e recompilado quando a próxima solicitação é recebida.  
  
-   Como código não compilado diretamente no arquivo .svc. Código de implementação também pode ser embutido localizado no arquivo. svc do serviço, após o @ServiceHost diretiva. As alterações ao código embutido fazem o aplicativo ser reciclado e recompilado quando a próxima solicitação é recebida.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]o [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] modelo de compilação, consulte [visão geral de compilação do ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94773).  
  
## <a name="configure-the-wcf-service"></a>Configurar o serviço WCF  
 Os serviços de configuração hospedados no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] armazenam sua configuração no arquivo Web.config do aplicativo. Os serviços hospedados no IIS usam os mesmos elementos e a sintaxe de configuração que os serviços do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hospedados fora do IIS. No entanto, as seguintes restrições são exclusivas para o ambiente de hospedagem do IIS:  
  
-   Endereços de base para serviços hospedados no IIS.  
  
-   Aplicativos que hospedem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços fora do IIS podem controlar o endereço base dos serviços que hospedam passando um conjunto de base de dados de endereço URIs para o <xref:System.ServiceModel.ServiceHost> construtor ou fornecendo um [ \<host >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) elemento de configuração do serviço. Os serviços hospedados no IIS não têm a capacidade de controlar seu endereço de base; o endereço de base de um serviço hospedado no IIS é o endereço de seu arquivo .svc.  
  
### <a name="endpoint-addresses-for-iis-hosted-services"></a>Endereços de ponto de extremidade para serviços hospedados no IIS  
 Quando estão hospedados no IIS, os endereços de ponto de extremidade são sempre considerados relativos para o endereço do arquivo .svc que representa o serviço. Por exemplo, se o endereço de base de um serviço do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] for http://localhost/Application1/MyService.svc com a seguinte configuração de ponto de extremidade.  
  
```xml  
<endpoint address="anotherEndpoint" .../>  
```  
  
 Isso fornece um ponto de extremidade que pode ser alcançado em "http://localhost/Application1/MyService.svc/anotherEndpoint".  
  
 Da mesma forma, o elemento de configuração do ponto de extremidade que usa uma cadeia de caracteres vazia como o endereço relativo fornece um ponto de extremidade alcançável em http://localhost/Application1/MyService.svc, que é o endereço de base.  
  
```xml  
<endpoint address="" ... />  
```  
  
 Você sempre deve usar endereços de ponto de extremidade relativos para pontos de extremidade de serviço hospedados no IIS. Fornecer um endereço de ponto de extremidade totalmente qualificado (por exemplo, http://localhost/MyService.svc) pode levar a erros na implantação do serviço se o endereço do ponto de extremidade não apontar para o aplicativo do IIS que hospeda o serviço que expõe o ponto de extremidade. Usar endereços de ponto de extremidade relativos para serviços hospedados evita esses conflitos em potencial.  
  
### <a name="available-transports"></a>Transportes disponíveis  
 Os serviços do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hospedados no IIS 5.1 e o [!INCLUDE[iis601](../../../../includes/iis601-md.md)] são restritos para usar a comunicação com base em HTTP. Nessas plataformas do IIS, configurar um serviço hospedado para usar uma associação não HTTP resulta em um erro durante a ativação do serviço. Para o [!INCLUDE[iisver](../../../../includes/iisver-md.md)], os transportes com suporte incluem HTTP, Net.TCP, Net.Pipe, Net.MSMQ e msmq.formatname para compatibilidade retroativa com os aplicativos existentes do MSMQ.  
  
### <a name="http-transport-security"></a>Segurança de transporte de HTTP  
 Os serviços do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hospedados no IIS podem utilizar a segurança de transporte do HTTP (por exemplo, esquemas de autenticação de HTTPS e HTTP como Básico, Resumido e Autenticação Integrada do Windows) contanto que o diretório virtual do IIS que contém os serviços dê suporte a essas configurações. As configurações de segurança de transporte de HTTP em uma associação do ponto de extremidade hospedado devem corresponder às configurações de segurança de transporte no diretório virtual do IIS que as contêm.  
  
 Por exemplo, um ponto de extremidade do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configurado para usar a autenticação resumida do HTTP deve residir em um diretório virtual do IIS que também seja configurado para permitir a autenticação resumida do HTTP. As combinações sem correspondência de configurações do IIS e configurações de ponto de extremidade do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] resultam em um erro durante a ativação do serviço.  
  
## <a name="see-also"></a>Consulte também  
 [Hospedagem no Internet Information Services](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Práticas recomendadas de hospedagem de serviços de informações da Internet](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
