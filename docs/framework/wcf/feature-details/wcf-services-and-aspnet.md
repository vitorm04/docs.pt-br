---
title: Serviços WCF e ASP.NET
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: 6cfd4f8a5dc2a7835cba409a37b09166e49e8df3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506157"
---
# <a name="wcf-services-and-aspnet"></a>Serviços WCF e ASP.NET
Este tópico discute hospedagem Windows Communication Foundation (WCF) serviços-lado a lado com o ASP.NET e hospedá-los no modo de compatibilidade do ASP.NET.  
  
## <a name="hosting-wcf-side-by-side-with-aspnet"></a>Hospedagem WCF lado a lado com o ASP.NET  
 Os serviços WCF hospedados no serviços de informações da Internet (IIS) podem ser localizados com. Páginas ASPX e serviços Web ASMX dentro de um domínio de aplicativo único, comuns. O ASP.NET fornece serviços de infraestrutura comuns, como gerenciamento de AppDomain e compilação dinâmica para o WCF e o tempo de execução HTTP do ASP.NET. A configuração padrão para o WCF é lado a lado com o ASP.NET.  
  
 ![Serviços WCF e ASP .NET: estado de compartilhamento](../../../../docs/framework/wcf/feature-details/media/hostingwcfwithaspnet.gif "HostingWCFwithASPNET")  
  
 O tempo de execução HTTP do ASP.NET manipula solicitações ASP.NET, mas não participa no processamento de solicitações destinadas a serviços WCF, mesmo que esses serviços são hospedados no mesmo AppDomain como o ASP.NET conteúdo. Em vez disso, o modelo de serviço WCF intercepta as mensagens destinadas a serviços WCF e encaminha-los por meio da pilha de transporte/canal WCF.  
  
 Os resultados do modelo lado a lado são da seguinte maneira:  
  
-   Serviços ASP.NET e WCF podem compartilhar o estado do AppDomain. Porque as duas estruturas podem coexistir no mesmo AppDomain, WCF também pode compartilhar o estado de AppDomain com o ASP.NET (incluindo variáveis estáticas, eventos e assim por diante).  
  
-   Serviços WCF se comportar de forma consistente, independente do transporte e o ambiente de hospedagem. O tempo de execução HTTP do ASP.NET intencionalmente é acoplado ao IIS/ASP.NET comunicação HTTP e ambiente de hospedagem. Por outro lado, o WCF foi projetado para se comportar de forma consistente em ambientes de hospedagem (WCF se comporta de forma consistente ambas dentro e fora do IIS) e em transporte (um serviço hospedado no IIS 7.0 e posterior tem um comportamento consistente em todos os pontos de extremidade que expõe, mesmo se Alguns desses pontos de extremidade usam protocolos que não sejam HTTP).  
  
-   Dentro de um AppDomain recursos implementados pelo tempo de execução HTTP se aplicam ao conteúdo do ASP.NET, mas não para o WCF. Não se aplicam a muitos recursos de HTTP específica da plataforma do aplicativo ASP.NET para serviços WCF hospedados dentro de um AppDomain que contém o conteúdo ASP.NET. Exemplos desses recursos incluem o seguinte:  
  
    -   HttpContext: <xref:System.Web.HttpContext.Current%2A> é sempre `null` quando acessada a partir de um serviço WCF. Use <!--zz <xref:System.ServiceModel.OperationContext.Current.RequestContext>--> `RequestContext` em vez disso.  
  
    -   Autorização baseada em arquivo: o modelo de segurança do WCF não permite que a lista de controle de acesso (ACL) aplicada ao arquivo. svc do serviço ao decidir se uma solicitação de serviço é autorizada.  
  
    -   Autorização de URL com base em configuração: Da mesma forma, o modelo de segurança do WCF não obedece às regras de autorização com base em URL especificadas em System. Web \<autorização > elemento de configuração. Essas configurações são ignoradas para solicitações WCF, se um serviço reside em um espaço de URL protegido por ASP. Regras de autorização de URL do NET.  
  
    -   Extensibilidade de HttpModule: infraestrutura de hospedagem o WCF intercepta WCF solicita quando o <xref:System.Web.HttpApplication.PostAuthenticateRequest> evento é gerado e não retorna o processamento para o pipeline HTTP do ASP.NET. Os módulos que são codificados para interceptar solicitações em etapas posteriores do pipeline não interceptar solicitações WCF.  
  
    -   Representação do ASP.NET: por padrão, WCF solicitações sempre é executado como o IIS processar identidade, mesmo que o ASP.NET é definido para habilitar a representação usando do System. Web \<representar identidade = "true" / > opção de configuração.  
  
 Essas restrições se aplicam apenas a serviços WCF hospedados no aplicativo do IIS. O comportamento do conteúdo do ASP.NET não é afetado pela presença de WCF.  
  
 Aplicativos WCF que exigem a funcionalidade tradicionalmente fornecida pelo pipeline HTTP devem considerar o uso os equivalentes WCF, que são o host e independentes de transporte:  
  
-   <xref:System.ServiceModel.OperationContext> em vez de <xref:System.Web.HttpContext>.  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> em vez de ASP. Autorização de URL do arquivo do NET.  
  
-   <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> ou canais em camadas personalizados em vez de módulos HTTP.  
  
-   Representação para cada operação usando o WCF, em vez de representação de System. Web.  
  
 Como alternativa, você pode considerar executar seus serviços no modo de compatibilidade do ASP.NET do WCF.  
  
## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>Hospedar serviços WCF no modo de compatibilidade do ASP.NET  
 Embora o modelo WCF foi projetado para se comportar consistentemente em transportes e ambientes de hospedagem, geralmente há situações em que um aplicativo não exigir esse grau de flexibilidade. Modo de compatibilidade do ASP.NET do WCF é adequado para cenários que não exigem a capacidade de hospedar fora do IIS ou para se comunicar através de protocolos que não sejam HTTP, mas que usar todos os recursos da plataforma do aplicativo Web do ASP.NET.  
  
 Ao contrário da configuração de lado a lado padrão, onde a infraestrutura de hospedagem do WCF intercepta mensagens do WCF e roteia fora o pipeline HTTP, serviços WCF em execução no modo de compatibilidade ASP.NET participarem totalmente o ciclo de vida de solicitação de HTTP do ASP.NET. No modo de compatibilidade, os serviços WCF usam o pipeline HTTP por meio de um <xref:System.Web.IHttpHandler> implementação, semelhante às solicitações de maneira para páginas ASPX e serviços Web ASMX são manipulados. Como resultado, WCF se comporta de forma idêntica para ASMX em relação aos seguintes recursos do ASP.NET:  
  
-   <xref:System.Web.HttpContext>: Serviços WCF em execução no modo de compatibilidade ASP.NET podem acessar <xref:System.Web.HttpContext.Current%2A> e seu estado associado.  
  
-   Autorização baseada em arquivo: serviços WCF em execução no modo de compatibilidade ASP.NET podem ser seguros, anexando listas de controle de acesso do sistema de arquivos (ACLs) para o arquivo do serviço. svc.  
  
-   Autorização de URL configurável: ASP. Regras de autorização de URL do NET são impostas para solicitações WCF, quando o serviço WCF estiver sendo executado no modo de compatibilidade do ASP.NET.  
  
-   <xref:System.Web.HttpModuleCollection> extensibilidade: serviços WCF porque executados no modo de compatibilidade ASP.NET participarem totalmente o ciclo de vida de solicitação de HTTP do ASP.NET, qualquer módulo HTTP configurado no pipeline HTTP pode operar em solicitações WCF antes e depois da invocação de serviço.  
  
-   Representação do ASP.NET: Serviços WCF executados usando a identidade atual do ASP.NET representada thread, que pode ser diferente do que a identidade de processo do IIS se a representação do ASP.NET foi habilitada para o aplicativo. Se a representação do ASP.NET e a representação de WCF são habilitadas para uma operação de serviço específico, a implementação do serviço é executado usando a identidade obtida do WCF.  
  
 Modo de compatibilidade do ASP.NET do WCF está habilitado no nível do aplicativo por meio de configuração a seguir (localizada no arquivo de Web. config do aplicativo):  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />  
</system.serviceModel>  
```  
  
 O valor padrão é "`true`" se não for especificado. Definir esse valor como "`false`" indica que todos os serviços do WCF em execução no aplicativo não serão executado no modo de compatibilidade do ASP.NET.  
  
 Porque o modo de compatibilidade ASP.NET implica a semântica de processamento de solicitação é fundamentalmente diferente do padrão WCF, implementações de serviço individuais têm a capacidade de controlar se eles são executados dentro de um aplicativo em que o ASP.NET Modo de compatibilidade foi habilitado. Os serviços podem usar o <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> para indicar se há suporte para o modo de compatibilidade do ASP.NET. O valor padrão para este atributo é <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>.  
  
 `[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]`  
  
 `public class CalculatorService : ICalculatorSession`  
  
 `{//Implement calculator service methods.}`  
  
 A tabela a seguir ilustra como a configuração de modo de compatibilidade de todo o aplicativo interage com o serviço individual indicado o nível de suporte:  
  
|Configuração do modo de compatibilidade de todo o aplicativo|[AspNetCompatibilityRequirementsMode]<br /><br /> Configuração|Resultados observados|  
|--------------------------------------------------|---------------------------------------------------------|---------------------|  
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Serviço ativado com êxito.|  
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Serviço ativado com êxito.|  
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Ocorrerá um erro de ativação quando o serviço recebe uma mensagem.|  
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Ocorrerá um erro de ativação quando o serviço recebe uma mensagem.|  
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Serviço ativado com êxito.|  
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Serviço ativado com êxito.|  
  
> [!NOTE]
>  IIS 7.0 e WAS permite que os serviços do WCF para se comunicar através de protocolos que não sejam HTTP. No entanto, os serviços WCF em execução em aplicativos que tem habilitado o modo de compatibilidade do ASP.NET não são permitidos para expor pontos de extremidade HTTP não. Essa configuração gera uma exceção de ativação quando o serviço recebe a primeira mensagem.  
  
 Para obter mais informações sobre como habilitar o modo de compatibilidade ASP.NET para serviços WCF, consulte <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> e [compatibilidade com ASP.NET](../../../../docs/framework/wcf/samples/aspnet-compatibility.md) exemplo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>  
 [Recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
