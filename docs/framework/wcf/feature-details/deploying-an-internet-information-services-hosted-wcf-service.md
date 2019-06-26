---
title: Implantando um Serviço WCF hospedado do Internet Information Services dos Serviços de Informações da Internet
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: 4c46a7ac0482e0f9c969505b87558d240bb1391e
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402294"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Implantando um Serviço WCF hospedado do Internet Information Services dos Serviços de Informações da Internet

Desenvolvendo e implantando um serviço do Windows Communication Foundation (WCF) que é hospedado no Internet Information Services (IIS) consiste as seguintes tarefas:

- Certifique-se de que o IIS, ASP.NET, WCF e o componente de ativação do WCF estão corretamente instalados e registrados.

- Criar um novo aplicativo do IIS ou reutilizar um aplicativo ASP.NET existente.

- Crie um arquivo. svc para o serviço WCF.

- Implantar a implementação do serviço para o aplicativo do IIS.

- Configure o serviço do WCF.

Para obter instruções detalhadas de criação de um serviço WCF hospedado pelo IIS, consulte [como: Hospedar um serviço WCF no IIS](how-to-host-a-wcf-service-in-iis.md).

## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>Verificar se o IIS, o ASP.NET, o WCF estão corretamente instalados e registrados

WCF, o IIS e o ASP.NET devem ser instalado para serviços WCF hospedados no IIS para funcionar corretamente. Os procedimentos para instalar o IIS, ASP.NET e WCF (como parte do .NET Framework) variam dependendo do sistema operacional. Para obter mais informações sobre como instalar o WCF e o .NET Framework, consulte [instalar o .NET Framework para desenvolvedores](../../install/guide-for-developers.md). Para instalar o IIS no Windows 10, abra **programas e recursos** na **painel de controle** e, em seguida, selecione **ativar ou desativar recursos do Windows ativar**. Na **recursos do Windows**, selecione **serviços de informações da Internet** e, em seguida, escolha **Okey**.

![Recursos do Windows com o IIS realçado](media/windows-features-iis.png)

Instruções para instalar o IIS em outros sistemas operacionais podem ser encontradas em [instalar o IIS no Windows Vista e Windows 7](/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7) e [instalar o IIS 8.5 no Windows Server 2012 R2](/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2).

O processo de instalação do .NET Framework registra automaticamente WCF com o IIS se o IIS já estiver presente no computador. Se o IIS for instalado após o .NET Framework, uma etapa adicional é necessário para registrar o WCF com o IIS e ASP.NET. Você pode fazer isso da seguinte maneira, dependendo do sistema operacional:

- O Windows 7 e Windows Server 2003: Use o [ferramenta de registro de ServiceModel (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) ferramenta para registrar o WCF com o IIS. Para usar essa ferramenta, digite **ServiceModelReg.exe /i /x** na [Prompt de comando do desenvolvedor para Visual Studio](../../tools/developer-command-prompt-for-vs.md).

- Windows 7: Por fim, você deve verificar se o ASP.NET está configurado para usar o .NET Framework versão 4 ou posterior. Você pode fazer isso executando a ferramenta ASPNET_Regiis com a `–i` opção. Para obter mais informações, consulte [ferramenta de registro ASP.NET IIS](https://go.microsoft.com/fwlink/?LinkId=201186).

## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Criar um novo aplicativo do IIS ou reutilizar um existente do ASP.NET

Os serviços WCF hospedados no IIS devem residir em um aplicativo do IIS. Você pode criar um novo aplicativo do IIS para hospedar serviços WCF exclusivamente. Como alternativa, você pode implantar um serviço WCF em um aplicativo existente que já está hospedando o conteúdo do ASP.NET 2.0 (como páginas. aspx e serviços Web do ASP.NET [ASMX]). Para obter mais informações sobre essas opções, consulte a "Hosting WCF lado a lado com o ASP.NET" e "Hospedagem WCF Services no modo de compatibilidade do ASP.NET" seções nas [serviços WCF e ASP.NET](wcf-services-and-aspnet.md).

Observe que o IIS 6.0 e versões posteriores periodicamente reiniciar um aplicativo isolado de programação orientada a objeto. O valor padrão é 1740 minutos. O valor máximo valor com suporte é 71.582 minutos. Esse reinício pode ser desabilitado. Para obter mais informações sobre essa propriedade, consulte a [{2&gt;{3&gt;PeriodicRestartTime&lt;3}&lt;2](https://go.microsoft.com/fwlink/?LinkId=109968).

## <a name="create-an-svc-file-for-the-wcf-service"></a>Criar um arquivo .svc para o serviço WCF

Serviços WCF hospedados no IIS são representados como arquivos especiais conteúdos (arquivos. svc) dentro do aplicativo do IIS. Esse modelo é semelhante à maneira como as páginas ASMX são representadas dentro de um aplicativo do IIS como arquivos .asmx. Um arquivo. svc contém uma diretiva de processamento específicas do WCF ([\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)) que permite que a infraestrutura de hospedagem do WCF ativar serviços hospedados em resposta às mensagens de entrada. A sintaxe mais comum para um arquivo .svc está na instrução a seguir.

```
<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>
```

Ele consiste na [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva e um único atributo, `Service`. O valor do atributo `Service` é o nome do tipo CLR (Common Language Runtime) da implementação do serviço. Usar essa diretiva é basicamente equivalente a criar um host de serviço usando o código a seguir.

```csharp
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );
```

A configuração de hospedagem adicional, como a criação de uma lista de endereços de base para o serviço também pode ser feita. Você também pode usar um <xref:System.ServiceModel.Activation.ServiceHostFactory> personalizado para estender a política para usar com soluções de hospedagem personalizadas. Os aplicativos do IIS que hospedam os serviços WCF não são responsáveis por gerenciar a criação e o tempo de vida de <xref:System.ServiceModel.ServiceHost> instâncias. A infraestrutura de hospedagem gerenciada WCF cria o necessário <xref:System.ServiceModel.ServiceHost> instância dinamicamente quando a primeira solicitação é recebida para o arquivo. svc. A instância não é liberada até que seja fechada explicitamente pelo código ou quando o aplicativo for reciclado.

Para obter mais informações sobre a sintaxe para arquivos. svc, consulte [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).

## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Implantar a implementação do serviço para o aplicativo do IIS

Os serviços WCF hospedados no IIS usam o mesmo modelo de compilação dinâmica como o ASP.NET 2.0. Assim como ocorre com ASP.NET, você pode implantar o código de implementação para os serviços WCF hospedados no IIS de várias maneiras em vários locais, da seguinte maneira:

- Como um arquivo .dll pré-compilado localizado no GAC (cache de assembly global) ou no diretório \bin do aplicativo. Os binários pré-compilados não são atualizados até que uma nova versão da biblioteca de classe seja implantada.

- Como arquivos de origem não compilados localizados no diretório de \App_Code do aplicativo. Os arquivos de origem localizados nesse diretório são exigidos dinamicamente ao processar a primeira solicitação do aplicativo. As alterações nos arquivos no diretório \App_Code fazem o aplicativo inteiro ser reciclado e recompilado quando a próxima solicitação é recebida.

- Como o código não compilado é colocado diretamente no arquivo. svc. Código de implementação também pode ser localizado embutido no arquivo. svc do serviço, após o \@diretiva ServiceHost. As alterações ao código embutido fazem o aplicativo ser reciclado e recompilado quando a próxima solicitação é recebida.

Para obter mais informações sobre o modelo de compilação do ASP.NET 2.0, consulte [visão geral de compilação do ASP.NET](https://go.microsoft.com/fwlink/?LinkId=94773).

## <a name="configure-the-wcf-service"></a>Configurar o serviço WCF

Os serviços WCF hospedados no IIS armazenam sua configuração no arquivo de Web. config do aplicativo. Serviços hospedados no IIS usam os mesmos elementos de configuração e a sintaxe como serviços WCF hospedados fora do IIS. No entanto, as seguintes restrições são exclusivas para o ambiente de hospedagem do IIS:

- Endereços de base para serviços hospedados no IIS.

- Os aplicativos de hospedagem de serviços WCF fora do IIS pode controlar o endereço básico de serviços que hospedam passando um conjunto de base de dados de endereço URIs para o <xref:System.ServiceModel.ServiceHost> construtor ou fornecendo uma [ \<host >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) elemento o configuração do serviço. Os serviços hospedados no IIS não têm a capacidade de controlar seu endereço de base; o endereço de base de um serviço hospedado no IIS é o endereço de seu arquivo .svc.

### <a name="endpoint-addresses-for-iis-hosted-services"></a>Endereços de ponto de extremidade para serviços hospedados no IIS

Quando estão hospedados no IIS, os endereços de ponto de extremidade são sempre considerados relativos para o endereço do arquivo .svc que representa o serviço. Por exemplo, se o endereço básico de um serviço WCF é `http://localhost/Application1/MyService.svc` com a seguinte configuração de ponto de extremidade:

```xml
<endpoint address="anotherEndpoint" .../>
```

Isso fornece um ponto de extremidade que pode ser contatado pelo `http://localhost/Application1/MyService.svc/anotherEndpoint`.

Da mesma forma, o elemento de configuração de ponto de extremidade que usa uma cadeia de caracteres vazia como o endereço relativo fornece um ponto de extremidade alcançável em `http://localhost/Application1/MyService.svc`, que é o endereço base.

```xml
<endpoint address="" ... />
```

Você sempre deve usar endereços de ponto de extremidade relativos para pontos de extremidade de serviço hospedados no IIS. Fornecendo um endereço de ponto de extremidade totalmente qualificado (por exemplo, `http://localhost/MyService.svc`) pode levar a erros na implantação do serviço se o endereço do ponto de extremidade não apontar para o aplicativo do IIS que hospeda o serviço expondo o ponto de extremidade. Usar endereços de ponto de extremidade relativos para serviços hospedados evita esses conflitos em potencial.

### <a name="available-transports"></a>Transportes disponíveis

Serviços do WCF hospedado no IIS 5.1 e 6.0 do IIS está restrito a usar a comunicação baseada em HTTP. Nessas plataformas do IIS, configurar um serviço hospedado para usar uma associação não HTTP resulta em um erro durante a ativação do serviço. Para o [!INCLUDE[iisver](../../../../includes/iisver-md.md)], os transportes com suporte incluem HTTP, Net.TCP, Net.Pipe, Net.MSMQ e msmq.formatname para compatibilidade retroativa com os aplicativos existentes do MSMQ.

### <a name="http-transport-security"></a>Segurança de transporte de HTTP

Os serviços WCF hospedados no IIS podem fazer uso do HTTP (por exemplo, HTTP e HTTPS esquemas de autenticação como básico, Digest e autenticação integrada do Windows) de segurança de transporte, desde que o diretório virtual IIS que contém o serviço dá suporte a aqueles Configurações. As configurações de segurança de transporte de HTTP em uma associação do ponto de extremidade hospedado devem corresponder às configurações de segurança de transporte no diretório virtual do IIS que as contêm.

Por exemplo, um ponto de extremidade do WCF configurado para usar a autenticação digest HTTP deve residir em um diretório virtual IIS que também está configurado para permitir a autenticação digest HTTP. Sem correspondência combinações de configurações do IIS e configurações de ponto de extremidade do WCF resultam em um erro durante a ativação do serviço.

## <a name="see-also"></a>Consulte também

- [Hospedagem nos Serviços de Informações da Internet](hosting-in-internet-information-services.md)
- [Práticas recomendadas de hospedagem de Serviços de Informações da Internet](internet-information-services-hosting-best-practices.md)
- [Recursos de hospedagem do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
