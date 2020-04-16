---
title: Implantando um Serviço WCF hospedado do Internet Information Services dos Serviços de Informações da Internet
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: 67f6877546951bd92b235218f10f6ccc7011ef5c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463862"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Implantando um Serviço WCF hospedado do Internet Information Services dos Serviços de Informações da Internet

Desenvolver e implantar um serviço da Windows Communication Foundation (WCF) hospedado no Internet Information Services (IIS) consiste nas seguintes tarefas:

- Certifique-se de que o IIS, ASP.NET, WCF e o componente de ativação do WCF estejam corretamente instalados e registrados.

- Crie um novo aplicativo IIS ou reutilize um aplicativo de ASP.NET existente.

- Crie um arquivo .svc para o serviço WCF.

- Implantar a implementação do serviço para o aplicativo do IIS.

- Configure o serviço WCF.

Para obter um passo a passo detalhado da criação de um serviço WCF hospedado pelo IIS, consulte [Como hospedar um serviço WCF no IIS](how-to-host-a-wcf-service-in-iis.md).

## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>Verificar se o IIS, o ASP.NET, o WCF estão corretamente instalados e registrados

O WCF, o IIS e o ASP.NET devem ser instalados para que os serviços WCF hospedados pelo IIS funcionem corretamente. Os procedimentos para instalar o WCF (como parte do Framework .NET), ASP.NET e IIS variam dependendo do seu sistema operacional. Para obter mais informações sobre a instalação do WCF e do .NET Framework, consulte [Instalar o .NET Framework para desenvolvedores](../../install/guide-for-developers.md). Para instalar o IIS no Windows 10, abra **Programas e Recursos** no **Painel de Controle** e selecione Ativar ou desativar os recursos do **Windows**. Em **Recursos do Windows,** selecione **Serviços de Informações da Internet** e escolha **OK**.

![Recursos do Windows com IIS destacado](./media/windows-features-iis.png)

Instruções para instalar iIS em outros sistemas operacionais podem ser encontradas no [Install IIS no Windows Vista e no Windows 7](/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7) e instalar o [IIS 8.5 no Windows Server 2012 R2](/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2).

O processo de instalação do .NET Framework registra automaticamente o WCF com o IIS se o IIS já estiver presente na máquina. Se o IIS for instalado após o .NET Framework, é necessário um passo adicional para registrar o WCF com o IIS e ASP.NET. Você pode fazer isso da seguinte maneira, dependendo do sistema operacional:

- Windows 7 e Windows Server 2003: Use a [ferramenta ServiceModel Registration Tool (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) para registrar o WCF com o IIS. Para usar esta ferramenta, **digite ServiceModelReg.exe /i /x** no [Prompt de comando do desenvolvedor para o Visual Studio](../../tools/developer-command-prompt-for-vs.md).

- Windows 7: Finalmente, você deve verificar se ASP.NET está configurado para usar a versão 4 ou posterior do .NET Framework. Você faz isso executando a `–i` ferramenta ASPNET_Regiis com a opção. Para obter mais informações, consulte [ASP.NET Ferramenta de Registro do IIS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90)).

## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Criar um novo aplicativo do IIS ou reutilizar um existente do ASP.NET

Os serviços WCF hospedados pelo IIS devem residir dentro de um aplicativo IIS. Você pode criar um novo aplicativo IIS para hospedar exclusivamente serviços WCF. Alternativamente, você pode implantar um serviço WCF em um aplicativo existente que já está hospedando conteúdo ASP.NET 2.0 (como páginas .aspx e serviços web ASP.NET [ASMX]). Para obter mais informações sobre essas opções, consulte as seções "Hosting WCF Side-by-Side with ASP.NET" e "Hosting WCF Services in ASP.NET Compatibility Mode" nos [Serviços WCF e ASP.NET](wcf-services-and-aspnet.md).

Observe que as versões IIS 6.0 e posteriores reiniciam periodicamente um aplicativo de programação isolado orientado a objetos. O valor padrão é 1740 minutos. O valor máximo valor com suporte é 71.582 minutos. Esse reinício pode ser desabilitado. Para obter mais informações sobre esta propriedade, consulte o [PeriodicRestartTime](https://docs.microsoft.com/previous-versions/iis/6.0-sdk/ms525914(v=vs.90)).

## <a name="create-an-svc-file-for-the-wcf-service"></a>Criar um arquivo .svc para o serviço WCF

Os serviços WCF hospedados no IIS são representados como arquivos de conteúdo especial (arquivos.svc) dentro do aplicativo IIS. Esse modelo é semelhante à maneira como as páginas ASMX são representadas dentro de um aplicativo do IIS como arquivos .asmx. Um arquivo .svc contém uma diretiva de processamento específica do WCF[\@(ServiceHost)](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)que permite que a infra-estrutura de hospedagem WCF ative os serviços hospedados em resposta às mensagens recebidas. A sintaxe mais comum para um arquivo .svc está na instrução a seguir.

`<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>`

Ele consiste `Service`na [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva ServiceHost e um único atributo, . O valor do atributo `Service` é o nome do tipo CLR (Common Language Runtime) da implementação do serviço. Usar essa diretiva é basicamente equivalente a criar um host de serviço usando o código a seguir.

```csharp
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );
```

A configuração de hospedagem adicional, como a criação de uma lista de endereços de base para o serviço também pode ser feita. Você também pode usar um <xref:System.ServiceModel.Activation.ServiceHostFactory> personalizado para estender a política para usar com soluções de hospedagem personalizadas. Os aplicativos IIS que hospedam serviços WCF não <xref:System.ServiceModel.ServiceHost> são responsáveis pelo gerenciamento da criação e da vida útil das instâncias. A infra-estrutura de hospedagem <xref:System.ServiceModel.ServiceHost> WCF gerenciada cria a instância necessária dinamicamente quando a primeira solicitação é recebida para o arquivo .svc. A instância não é liberada até que seja fechada explicitamente pelo código ou quando o aplicativo for reciclado.

Para obter mais informações sobre a sintaxe para arquivos .svc, consulte [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).

## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Implantar a implementação do serviço para o aplicativo do IIS

Os serviços wcf hospedados no IIS usam o mesmo modelo de compilação dinâmica que ASP.NET 2.0. Assim como com ASP.NET, você pode implantar o código de implementação para serviços WCF hospedados pelo IIS de várias maneiras em vários locais, da seguinte forma:

- Como um arquivo .dll pré-compilado localizado no GAC (cache de assembly global) ou no diretório \bin do aplicativo. Os binários pré-compilados não são atualizados até que uma nova versão da biblioteca de classe seja implantada.

- Como arquivos de origem não compilados localizados no diretório \App_Code do aplicativo. Os arquivos de origem localizados nesse diretório são exigidos dinamicamente ao processar a primeira solicitação do aplicativo. As alterações nos arquivos no diretório \App_Code fazem o aplicativo inteiro ser reciclado e recompilado quando a próxima solicitação é recebida.

- Como código não compilado colocado diretamente no arquivo .svc. O código de implementação também pode ser localizado inline no \@arquivo .svc do serviço, após a diretiva ServiceHost. As alterações ao código embutido fazem o aplicativo ser reciclado e recompilado quando a próxima solicitação é recebida.

Para obter mais informações sobre o modelo de compilação ASP.NET 2.0, consulte [ASP.NET Visão Geral da Compilação](https://docs.microsoft.com/previous-versions/aspnet/ms178466(v=vs.100)).

## <a name="configure-the-wcf-service"></a>Configurar o serviço WCF

Os serviços WCF hospedados no IIS armazenam sua configuração no arquivo Web.config de aplicativos. Os serviços hospedados no IIS usam os mesmos elementos de configuração e sintaxe que os serviços WCF hospedados fora do IIS. No entanto, as seguintes restrições são exclusivas para o ambiente de hospedagem do IIS:

- Endereços de base para serviços hospedados no IIS.

- Os aplicativos que hospedam serviços WCF fora do IIS podem controlar o endereço base <xref:System.ServiceModel.ServiceHost> dos serviços que hospedam, passando um conjunto de URIs de endereço base para o construtor ou fornecendo um [ \<elemento host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) na configuração do serviço. Os serviços hospedados no IIS não têm a capacidade de controlar seu endereço de base; o endereço de base de um serviço hospedado no IIS é o endereço de seu arquivo .svc.

### <a name="endpoint-addresses-for-iis-hosted-services"></a>Endereços de ponto de extremidade para serviços hospedados no IIS

Quando estão hospedados no IIS, os endereços de ponto de extremidade são sempre considerados relativos para o endereço do arquivo .svc que representa o serviço. Por exemplo, se o endereço base `http://localhost/Application1/MyService.svc` de um serviço WCF estiver com a seguinte configuração de ponto final:

```xml
<endpoint address="anotherEndpoint" />
```

Isso fornece um ponto final `http://localhost/Application1/MyService.svc/anotherEndpoint`que pode ser alcançado em .

Da mesma forma, o elemento de configuração de ponto final que `http://localhost/Application1/MyService.svc`usa uma seqüência de string vazia como o endereço relativo fornece um ponto final acessível em , que é o endereço base.

```xml
<endpoint address="" />
```

Você sempre deve usar endereços de ponto de extremidade relativos para pontos de extremidade de serviço hospedados no IIS. Fornecer um endereço de ponto final totalmente `http://localhost/MyService.svc`qualificado (por exemplo, ) pode levar a erros na implantação do serviço se o endereço de ponto final não apontar para o aplicativo IIS que hospeda o serviço expondo o ponto final. Usar endereços de ponto de extremidade relativos para serviços hospedados evita esses conflitos em potencial.

### <a name="available-transports"></a>Transportes disponíveis

Os serviços WCF hospedados no IIS 5.1 e no IIS 6.0 estão restritos ao uso de comunicação baseada em HTTP. Nessas plataformas do IIS, configurar um serviço hospedado para usar uma associação não HTTP resulta em um erro durante a ativação do serviço. Para o IIS 7.0, os transportes suportados incluem HTTP, Net.TCP, Net.Pipe, Net.MSMQ e msmq.formatname para retrocompatibilidade com aplicativos MSMQ existentes.

### <a name="http-transport-security"></a>Segurança de transporte de HTTP

Os serviços WCF hospedados no IIS podem fazer uso da segurança de transporte HTTP (por exemplo, esquemas de autenticação HTTPS e HTTP, como Autenticação Integrada Básica, Digest e Windows), desde que o diretório virtual IIS que contém o serviço suporte essas configurações. As configurações de segurança de transporte de HTTP em uma associação do ponto de extremidade hospedado devem corresponder às configurações de segurança de transporte no diretório virtual do IIS que as contêm.

Por exemplo, um ponto final wcf configurado para usar autenticação http digest deve residir em um diretório virtual IIS que também está configurado para permitir a autenticação http digest. Combinações incomparáveis de configurações de IIS e configurações de ponto final do WCF resultam em um erro durante a ativação do serviço.

## <a name="see-also"></a>Confira também

- [Hospedagem no Internet Information Services](hosting-in-internet-information-services.md)
- [Práticas recomendadas de hospedagem de Serviços de Informações da Internet](internet-information-services-hosting-best-practices.md)
- [Recursos de hospedagem do Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
