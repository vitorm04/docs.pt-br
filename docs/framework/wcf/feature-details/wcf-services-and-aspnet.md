---
title: "Serviços WCF e ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: efa21ed4781cf635c5b49ebda9b13711a032e981
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-services-and-aspnet"></a>Serviços WCF e ASP.NET
Este tópico discute a hospedagem [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services lado a lado com o ASP.NET e hospedá-los no modo de compatibilidade do ASP.NET.  
  
## <a name="hosting-wcf-side-by-side-with-aspnet"></a>Hospedagem WCF lado a lado com o ASP.NET  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]serviços hospedados em serviços de informações da Internet (IIS) podem ser localizados com. Páginas ASPX e serviços Web ASMX dentro de um domínio de aplicativo único, comuns. O ASP.NET fornece serviços de infraestrutura comuns, como gerenciamento de AppDomain e compilação dinâmica para ambos [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e o tempo de execução HTTP do ASP.NET. A configuração padrão para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é lado a lado com o ASP.NET.  
  
 ![Serviços WCF e ASP .NET: estado de compartilhamento](../../../../docs/framework/wcf/feature-details/media/hostingwcfwithaspnet.gif "HostingWCFwithASPNET")  
  
 O tempo de execução HTTP do ASP.NET manipula solicitações ASP.NET, mas não participa no processamento de solicitações destinadas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, embora esses serviços são hospedados no mesmo AppDomain como o ASP.NET conteúdo. Em vez disso, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de serviço intercepta as mensagens destinadas a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços e encaminha-los por meio de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pilha de transporte/canais.  
  
 Os resultados do modelo lado a lado são da seguinte maneira:  
  
-   ASP.NET e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços podem compartilhar o estado do AppDomain. Porque as duas estruturas podem coexistir no mesmo AppDomain [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] também pode compartilhar o estado do AppDomain com ASP.NET (incluindo variáveis estáticas, eventos e assim por diante).  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Serviços de se comportar de forma consistente, independente do transporte e o ambiente de hospedagem. O tempo de execução HTTP do ASP.NET intencionalmente é acoplado ao IIS/ASP.NET comunicação HTTP e ambiente de hospedagem. Por outro lado, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] foi projetado para se comportar de forma consistente em ambientes de hospedagem ([!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se comporta de forma consistente ambas dentro e fora do IIS) e em transporte (um serviço hospedado no IIS 7.0 e posterior tem um comportamento consistente em todos os pontos de extremidade, ele expõe, mesmo se alguns desses pontos de extremidade usam protocolos diferentes de HTTP).  
  
-   Dentro de um AppDomain recursos implementados pelo tempo de execução HTTP se aplicam ao conteúdo do ASP.NET, mas não para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Muitos recursos de HTTP específica da plataforma do aplicativo ASP.NET não se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços hospedados dentro de um AppDomain que contém o conteúdo ASP.NET. Exemplos desses recursos incluem o seguinte:  
  
    -   HttpContext: <xref:System.Web.HttpContext.Current%2A> é sempre `null` quando acessadas de dentro um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço. Use <!--zz <xref:System.ServiceModel.OperationContext.Current.RequestContext>--> `RequestContext` em vez disso.  
  
    -   Autorização baseada em arquivo: O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de segurança não permite que a lista de controle de acesso (ACL) aplicada ao arquivo. svc do serviço ao decidir se uma solicitação de serviço é autorizada.  
  
    -   Autorização de URL com base em configuração: Da mesma forma, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de segurança não obedece às regras de autorização com base em URL especificadas em System. Web \<autorização > elemento de configuração. Essas configurações são ignoradas para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] solicitações se um serviço reside em um espaço de URL protegido por ASP. Regras de autorização de URL do NET.  
  
    -   Extensibilidade de HttpModule: O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] interseções de infraestrutura de hospedagem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] solicita quando o <xref:System.Web.HttpApplication.PostAuthenticateRequest> evento é gerado e não retorna o processamento para o pipeline HTTP do ASP.NET. Os módulos que são codificados para interceptar solicitações em etapas posteriores do pipeline não interceptar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] solicitações.  
  
    -   Representação do ASP.NET: por padrão, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] solicitações sempre é executado como o IIS processar identidade, mesmo que o ASP.NET é definido para habilitar a representação usando do System. Web \<representar identidade = "true" / > opção de configuração.  
  
 Essas restrições se aplicam somente ao [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços hospedados no aplicativo do IIS. O comportamento do conteúdo do ASP.NET não é afetado pela presença de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]aplicativos que exigem a funcionalidade tradicionalmente fornecida pelo pipeline HTTP devem considerar o uso de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] equivalentes, o host e independentes de transporte:  
  
-   <xref:System.ServiceModel.OperationContext>em vez de <xref:System.Web.HttpContext>.  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>em vez de ASP. Autorização de URL do arquivo do NET.  
  
-   <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector>ou canais em camadas personalizados em vez de módulos HTTP.  
  
-   Representação para cada operação usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em vez de representação de System. Web.  
  
 Como alternativa, você pode considerar executar seus serviços [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do modo de compatibilidade do ASP.NET.  
  
## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>Hospedar serviços WCF no modo de compatibilidade do ASP.NET  
 Embora o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo foi projetado para se comportar consistentemente em transportes e ambientes de hospedagem, geralmente há situações em que um aplicativo não exigir esse grau de flexibilidade. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do modo de compatibilidade ASP.NET é adequado para cenários que não exigem a capacidade de hospedar fora do IIS ou para se comunicar através de protocolos que não sejam HTTP, mas que usar todos os recursos da plataforma do aplicativo Web do ASP.NET.  
  
 Ao contrário da configuração padrão lado a lado, onde o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] interseções de infraestrutura de hospedagem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mensagens e encaminha-os fora do pipeline de HTTP, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços em execução no modo de compatibilidade ASP.NET participarem totalmente em o ciclo de vida de solicitação de HTTP do ASP.NET. No modo de compatibilidade, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços usam o pipeline HTTP por meio de um <xref:System.Web.IHttpHandler> implementação, semelhante às solicitações de maneira para páginas ASPX e serviços Web ASMX são manipulados. Como resultado, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se comporta de forma idêntica a ASMX com relação aos seguintes recursos do ASP.NET:  
  
-   <xref:System.Web.HttpContext>: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podem acessar serviços em execução no modo de compatibilidade ASP.NET <xref:System.Web.HttpContext.Current%2A> e seu estado associado.  
  
-   Autorização baseada em arquivo: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços em execução no modo de compatibilidade ASP.NET podem ser seguros, anexando listas de controle de acesso do sistema de arquivos (ACLs) para o arquivo do serviço. svc.  
  
-   Autorização de URL configurável: ASP. Regras de autorização de URL do NET são impostas para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] solicita quando o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço está em execução no modo de compatibilidade do ASP.NET.  
  
-   <xref:System.Web.HttpModuleCollection>extensibilidade: porque [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços em execução no modo de compatibilidade ASP.NET participarem totalmente o ciclo de vida de solicitação de HTTP do ASP.NET, qualquer módulo HTTP configurado no pipeline HTTP pode operar em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] solicitações antes e depois invocação de serviço.  
  
-   Representação do ASP.NET: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] os serviços são executados usando a identidade atual do ASP.NET representado thread, que pode ser diferente do que a identidade de processo do IIS se a representação do ASP.NET foi habilitada para o aplicativo. Se a representação do ASP.NET e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] representação estão habilitados para uma operação de serviço específico, a implementação do serviço é executado usando a identidade obtida [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do modo de compatibilidade ASP.NET está habilitado no nível do aplicativo por meio de configuração a seguir (localizada no arquivo de Web. config do aplicativo):  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />  
</system.serviceModel>  
```  
  
 O valor padrão é "`true`" se não for especificado. Definir esse valor como "`false`" indica que todos os [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços em execução no aplicativo não serão executado no modo de compatibilidade do ASP.NET.  
  
 Porque o modo de compatibilidade ASP.NET implica a semântica de processamento de solicitação é fundamentalmente diferente de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] padrão, implementações de serviço individuais têm a capacidade de controlar se eles são executados dentro de um aplicativo em qual ASP. Modo de compatibilidade do NET foi habilitado. Os serviços podem usar o <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> para indicar se há suporte para o modo de compatibilidade do ASP.NET. O valor padrão para este atributo é <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>.  
  
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
>  Permite que o IIS 7.0 e WAS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços para se comunicar através de protocolos que não sejam HTTP. No entanto, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços em execução em aplicativos que tem habilitado o modo de compatibilidade do ASP.NET não são permitidos para expor pontos de extremidade não HTTP. Essa configuração gera uma exceção de ativação quando o serviço recebe a primeira mensagem.  
  
 Para obter mais informações sobre como habilitar o modo de compatibilidade ASP.NET [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços, consulte <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> e [compatibilidade com ASP.NET](../../../../docs/framework/wcf/samples/aspnet-compatibility.md) exemplo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>  
 [Recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
