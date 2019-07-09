---
title: Serviços WCF e ASP.NET
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: d42787492b00b8e0a5a732d641947fec61b5ff96
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663675"
---
# <a name="wcf-services-and-aspnet"></a>Serviços WCF e ASP.NET

Este tópico discute hospedagem Windows Communication Foundation (WCF) serviços lado a lado com o ASP.NET e os hospeda em modo de compatibilidade do ASP.NET.

## <a name="hosting-wcf-side-by-side-with-aspnet"></a>Hospedando o WCF lado a lado com o ASP.NET

Os serviços WCF hospedados no Internet Information Services (IIS) podem ser localizados com. Páginas ASPX e Web services ASMX dentro de um domínio de aplicativo único e comuns. O ASP.NET fornece serviços de infraestrutura comuns, como gerenciamento de AppDomain e compilação dinâmica para o WCF e o tempo de execução HTTP do ASP.NET. A configuração padrão do WCF é lado a lado com o ASP.NET.

![Captura de tela mostrando os serviços WCF e ASP .NET: estado de compartilhamento.](./media/wcf-services-and-aspnet/windows-communication-foundation-services-asp-dotnet-configuration.gif)

O tempo de execução HTTP do ASP.NET manipula as solicitações do ASP.NET, mas não participa no processamento de solicitações destinadas para os serviços WCF, mesmo que esses serviços são hospedados no mesmo AppDomain, como é o conteúdo ASP.NET. Em vez disso, o modelo de serviço WCF intercepta mensagens endereçadas a serviços WCF e encaminha-as por meio da pilha de canal de transporte/do WCF.

Os resultados do modelo lado a lado são da seguinte maneira:

- Serviços ASP.NET e WCF podem compartilhar o estado de AppDomain. Porque as duas estruturas podem coexistir no mesmo AppDomain, o WCF também pode compartilhar o estado do AppDomain com o ASP.NET (incluindo variáveis estáticas, eventos e assim por diante).

- Os serviços WCF se comportam de forma consistente, independente do transporte e o ambiente de hospedagem. O tempo de execução HTTP do ASP.NET é intencionalmente ligado para a comunicação HTTP e ambiente de hospedagem IIS/ASP.NET. Por outro lado, o WCF foi projetado para se comportar de forma consistente entre ambientes de hospedagem (WCF se comporta de forma consistente tanto dentro e fora do IIS) e em transporte (um serviço hospedado no IIS 7.0 e posterior tem um comportamento consistente entre todos os pontos de extremidade que ele expõe, mesmo que Alguns desses pontos de extremidade usam protocolos diferentes de HTTP).

- Dentro de um AppDomain, recursos implementados pelo tempo de execução HTTP se aplicam ao conteúdo do ASP.NET, mas não para o WCF. Muitos recursos de HTTP específica da plataforma do aplicativo ASP.NET não se aplicam aos serviços do WCF hospedado dentro de um AppDomain que contém o conteúdo ASP.NET. Exemplos desses recursos incluem o seguinte:

  - HttpContext: <xref:System.Web.HttpContext.Current%2A> é sempre `null` quando acessada de dentro de um serviço WCF. Use <xref:System.ServiceModel.Channels.RequestContext> em seu lugar.

  - Autorização baseada em arquivo: O modelo de segurança do WCF não permite a lista de controle de acesso (ACL) aplicada ao arquivo. svc do serviço ao decidir se uma solicitação de serviço é autorizada.

  - Autorização baseada em configuração de URL: Da mesma forma, o modelo de segurança do WCF não adere à quaisquer regras de autorização baseada em URL especificadas do System. Web \<autorização > elemento de configuração. Essas configurações serão ignoradas para solicitações WCF, se um serviço reside em um espaço de URL protegido pelo ASP. Regras de autorização de URL da rede.

  - Extensibilidade de HttpModule: A infraestrutura de hospedagem do WCF intercepta o WCF solicita quando o <xref:System.Web.HttpApplication.PostAuthenticateRequest> evento é gerado e não retorna o processamento para o pipeline HTTP do ASP.NET. Os módulos que são codificados para interceptar solicitações em estágios posteriores do pipeline não interceptar solicitações do WCF.

  - Personificação do ASP.NET: Por padrão, WCF solicita sempre é executado como o IIS processar identidade, mesmo que o ASP.NET é definido para habilitar a representação usando System. Web \<identity impersonate = "true" / > opção de configuração.

Essas restrições se aplicam apenas a serviços WCF hospedados no aplicativo do IIS. O comportamento do conteúdo do ASP.NET não é afetado pela presença do WCF.

Os aplicativos do WCF que exigem a funcionalidade tradicionalmente fornecida pelo pipeline de HTTP devem considerar usando os equivalentes WCF, que são host e independentes de transporte:

- <xref:System.ServiceModel.OperationContext> em vez de <xref:System.Web.HttpContext>.

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> em vez de ASP. Autorização de URL do arquivo da rede.

- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> ou canais personalizados de em camadas, em vez de módulos HTTP.

- Representação para cada operação usando o WCF em vez da representação de System. Web.

Como alternativa, você pode considerar a execução de seus serviços no modo de compatibilidade do ASP.NET do WCF.

## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>Hospedando serviços WCF no modo de compatibilidade do ASP.NET

Embora o modelo WCF foi projetado para se comportar de forma consistente em transportes e ambientes de hospedagem, geralmente há situações em que um aplicativo não exige esse grau de flexibilidade. Modo de compatibilidade do ASP.NET do WCF é adequado para cenários que não exigem a capacidade de host fora do IIS ou para se comunicar por meio de protocolos diferentes de HTTP, mas que usam todos os recursos da plataforma do aplicativo Web do ASP.NET.

Ao contrário da configuração de lado a lado padrão, em que a infraestrutura de hospedagem do WCF intercepta mensagens do WCF e os direciona fora do pipeline de HTTP, os serviços WCF executados no modo de compatibilidade do ASP.NET participarem totalmente do ciclo de vida de solicitação HTTP do ASP.NET. No modo de compatibilidade, os serviços WCF usam o pipeline HTTP por meio de um <xref:System.Web.IHttpHandler> implementação, semelhante às solicitações de maneira para páginas ASPX e serviços Web ASMX são manipulados. Como resultado, o WCF comporta-se identicamente para ASMX em relação aos seguintes recursos do ASP.NET:

- <xref:System.Web.HttpContext>: Os serviços WCF executados no modo de compatibilidade do ASP.NET podem acessar <xref:System.Web.HttpContext.Current%2A> e seu estado associado.

- Autorização baseada em arquivo: Os serviços WCF executados no modo de compatibilidade do ASP.NET podem ser seguros, anexando as listas de controle de acesso do sistema de arquivos (ACLs) para o arquivo do serviço. svc.

- Autorização de URL configurável: ASP. As regras de autorização de URL da rede são impostas para solicitações WCF quando o serviço WCF estiver sendo executado no modo de compatibilidade do ASP.NET.

- <xref:System.Web.HttpModuleCollection> extensibilidade: Porque os serviços WCF executados no modo de compatibilidade do ASP.NET participarem totalmente do ciclo de vida de solicitação HTTP do ASP.NET, qualquer módulo HTTP configurado no pipeline de HTTP é capaz de operar em solicitações WCF, antes e depois da invocação de serviço.

- Personificação do ASP.NET: Os serviços WCF executados usando a identidade do ASP.NET atual representada thread, que pode ser diferente da identidade de processo do IIS se personificação do ASP.NET tiver sido habilitada para o aplicativo. Se a representação do ASP.NET e a representação de WCF estão habilitados para uma operação de serviço em particular, a implementação do serviço, por fim, é executado usando a identidade obtida do WCF.

Modo de compatibilidade do ASP.NET do WCF está habilitado no nível do aplicativo por meio de configuração a seguir (localizada no arquivo de Web. config do aplicativo):

```xml
<system.serviceModel>
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```

O valor padrão é "`true`" se não for especificado. Definir esse valor como "`false`" indica que todos os serviços WCF em execução no aplicativo não serão executado no modo de compatibilidade do ASP.NET.

Porque o modo de compatibilidade ASP.NET implica a semântica de processamento de solicitação é fundamentalmente diferente do padrão WCF, implementações de serviço individuais têm a capacidade de controle, estejam eles sendo executados dentro de um aplicativo para o qual o ASP.NET Modo de compatibilidade foi habilitado. Os serviços podem usar o <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> para indicar se há suporte para o modo de compatibilidade do ASP.NET. O valor padrão para esse atributo é <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>.

```csharp
[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
public class CalculatorService : ICalculatorSession
{//Implement calculator service methods.}
```

A tabela a seguir ilustra como a configuração do modo de compatibilidade de todo o aplicativo interage com o serviço individual indicado o nível de suporte:

|Configuração do modo de compatibilidade de todo o aplicativo|[AspNetCompatibilityRequirementsMode]<br /><br /> Configuração|Resultados observados|
|--------------------------------------------------|---------------------------------------------------------|---------------------|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Serviço é ativado com êxito.|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Serviço é ativado com êxito.|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Ocorrerá um erro de ativação quando o serviço recebe uma mensagem.|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Ocorrerá um erro de ativação quando o serviço recebe uma mensagem.|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Serviço é ativado com êxito.|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Serviço é ativado com êxito.|

> [!NOTE]
> O IIS 7.0 e WAS permite que os serviços do WCF para se comunicar por meio de protocolos diferentes de HTTP. No entanto, os serviços WCF executados em aplicativos que tem habilitado o modo de compatibilidade do ASP.NET não são permitidos para expor pontos de extremidade HTTP não. Essa configuração gera uma exceção de ativação quando o serviço recebe sua primeira mensagem.

Para obter mais informações sobre como habilitar o modo de compatibilidade do ASP.NET para serviços WCF, consulte <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> e o [compatibilidade ASP.NET](../samples/aspnet-compatibility.md) exemplo.

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>
- [Recursos de hospedagem do Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
