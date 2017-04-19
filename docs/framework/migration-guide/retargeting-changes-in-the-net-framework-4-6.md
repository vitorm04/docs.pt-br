---
title: "Alterações de redirecionamento no .NET Framework 4.6 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes, .NET Framework
- retargeting changes, .NET Framework 4.6
- application compatibility
ms.assetid: fa849255-f90f-4bf1-b0ff-b173c12110d7
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 19ad80233a79a4fdef89550696c1c3d33e14b355
ms.lasthandoff: 04/18/2017

---
# <a name="retargeting-changes-in-the-net-framework-46"></a>Alterações de redirecionamento no .NET Framework 4.6
Em casos raros, alterações de redirecionamento podem afetar aplicativos recompilados para segmentar o [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. A menos que indicado de outra forma, essas mudanças não afetam os binários direcionados a uma versão anterior do .NET Framework, mas que são executados no [!INCLUDE[net_v46](../../../includes/net-v46-md.md)].  
  
 O [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] inclui alterações de redirecionamento nas seguintes áreas:  
  
-   [Core](#Core)  
  
-   [ASP.NET](#ASP)  
  
-   [Rede](#Net)  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows Forms](#WinForms)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
-   [XML](#XML)  
  
<a name="Core"></a>   
## <a name="core"></a>Núcleo  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>, <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> e operações assíncronas baseadas em tarefa com <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601>|Para aplicativos direcionados ao [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] e versões posteriores, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> são armazenados em um <xref:System.Threading.ExecutionContext> do thread, que flui entre as operações assíncronas.|As alterações nas propriedades <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> serão refletidas em tarefas assíncronas que são inicializadas subsequentemente. Para saber mais, confira [Mitigation: Culture and Asynchronous Operations](../../../docs/framework/migration-guide/mitigation-culture-and-asynchronous-operations.md) (Mitigação: cultura e operações assíncronas).|Secundário|  
  
<a name="ASP"></a>   
## <a name="aspnet"></a>ASP.NET  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|<xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName> com um valor `tagKey` de <xref:System.Web.UI.HtmlTextWriterTag?displayProperty=fullName>|Em conformidade com o padrão HTML, o método <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName> agora renderiza <xref:System.Web.UI.HtmlTextWriterTag?displayProperty=fullName> como uma marca de não fechamento em uma resposta HTML.|A marca BR agora produz uma quebra de linha. Anteriormente, ela produzia duas quebras de linha.<br /><br /> Os aplicativos que dependem da marca `<BR>` para produzir duas quebras de linha podem restaurar o comportamento anterior adicionando uma chamada extra ao método <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName> com o argumento <xref:System.Web.UI.HtmlTextWriterTag?displayProperty=fullName>.|Secundário|  
  
<a name="Net"></a>   
## <a name="networking"></a>Rede  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|<xref:System.Net.ServicePointManager?displayProperty=fullName> e <xref:System.Net.Security.SslStream?displayProperty=fullName>|Começando com os aplicativos direcionados ao .NET Framework 4.6, as classes <xref:System.Net.ServicePointManager?displayProperty=fullName> e <xref:System.Net.Security.SslStream?displayProperty=fullName> têm permissão para usar um destes três protocolos: Tls1.0, Tls1.1 ou Tls 1.2.<br /><br /> Os aplicativos direcionados a uma versão anterior do .NET Framework, mesmo que eles sejam executados no NET Framework 4.6, não são afetados.|Essa alteração afeta qualquer aplicativo direcionado ao .NET Framework 4.6 e que usa o SSL para se comunicar com um servidor HTTPS ou um servidor de soquete usando qualquer um dos seguintes tipos: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient> e <xref:System.Net.Security.SslStream>.  Para saber mais, confira [Mitigation: TLS Protocols](../../../docs/framework/migration-guide/mitigation-tls-protocols.md) (Mitigação: protocolos TLS).|Secundário|  
  
<a name="WCF"></a>   
## <a name="windows-communications-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|<xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%2A?displayProperty=fullName>|A implementação do <xref:System.IdentityModel.Policy.AuthorizationContext> retornado por uma chamada ao <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29> com um argumento `null``authorizationPolicies` alterou sua implementação no [!INCLUDE[net_v46](../../../includes/net-v46-md.md)].|Em casos raros, os aplicativos WCF que usam a autenticação personalizada podem ver diferenças de comportamento. Se o comportamento antigo for necessário, confira [Mitigation: Default AuthorizationContext](../../../docs/framework/migration-guide/mitigation-default-authorizationcontext.md) (Mitigação: AuthorizationContext padrão).|Secundário|  
  
<a name="WinForms"></a>   
## <a name="windows-forms"></a>Windows Forms  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName>|Começando com os aplicativos direcionados ao .NET Framework 4.6, o método <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> converte com êxito ícones com quadros PNG em objetos <xref:System.Drawing.Bitmap>.<br /><br /> Em aplicativos direcionados ao .NET Framework 4.5.2 e versões anteriores, o método <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> vai gerar uma exceção <xref:System.ArgumentOutOfRangeException> se o objeto <xref:System.Drawing.Icon> tiver quadros PNG.|Essa alteração afeta aplicativos que são recompilados para direcionamento ao .NET Framework 4.6 e que fornecem tratamento especial para a exceção <xref:System.ArgumentOutOfRangeException> que será gerada se um objeto <xref:System.Drawing.Icon> tiver quadros PNG. Se esse comportamento for indesejável, uma opção de configuração restaura o comportamento anterior. Para saber mais, confira [Mitigation: PNG Frames in Icon Objects](../../../docs/framework/migration-guide/mitigation-png-frames-in-icon-objects.md) (Mitigação: quadros PNG em objetos de ícone).|Secundário|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>|Em aplicativos direcionados ao .NET Framework 4.6 e ao .NET Framework 4.6.1, as alterações nas propriedades <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> que são feitas em um <xref:System.Windows.Threading.Dispatcher> são perdidas no fim dessa operação de dispatcher. De modo semelhante, as alterações em <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> feitas fora de uma operação de dispatcher podem não ser refletidas quando essa operação for executada.|As alterações nas propriedades <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> podem não fluir entre os retornos de chamada da interface do usuário do WPF e outro código em um aplicativo WPF. Para saber mais, confira [Mitigation: Culture and Dispatcher Operations in WPF Apps](../../../docs/framework/migration-guide/mitigation-culture-and-dispatcher-operations-in-wpf-apps.md) (Mitigação: cultura e operações de dispatcher em aplicativos WPF).|Secundário|  
|Arredondamento de layout em altas DPIs|A maneira como as margens são arredondadas, bem como as bordas e a tela de fundo dentro delas, foi alterada.|O layout dos controles do WPF pode ser ligeiramente alterado. Para saber mais, confira [Mitigação: layout de WPF](../../../docs/framework/migration-guide/mitigation-wpf-layout.md).|Secundário|  
  
<a name="XML"></a>   
## <a name="xml"></a>XML  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Validação do esquema XSD|A partir do .NET Framework 4.6, a validação de esquema XSD detectará violação da restrição exclusiva se uma chave composta for usada e uma chave estiver vazia.|Confira [Mitigação: validação de esquema XML](../../../docs/framework/migration-guide/mitigation-xml-schema-validation.md)|Secundário|  
|<xref:System.Xml.XmlWriter>|Em aplicativos direcionados ao NET Framework 4.5.2 ou versões anteriores, escrever um par alternativo inválido usando o tratamento de fallback de exceção nem sempre gera uma exceção.<br /><br /> Em aplicativos direcionados ao [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], tentar escrever um par alternativo inválido gera uma exceção <xref:System.ArgumentException> .|Os aplicativos que são recompilados para direcionamento ao [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] e que escrevem pares alternativos inválidos vão gerar uma exceção em casos em que anteriormente não geravam.|Edge|
