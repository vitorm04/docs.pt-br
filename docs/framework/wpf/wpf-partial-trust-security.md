---
title: Segurança parcialmente confiável do WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- partial trust security [WPF]
- detecting permissions [WPF]
- security settings for Internet Explorer [WPF]
- partial trust applications [WPF], debugging
- permissions [WPF], managing
- debugging partial trust applications [WPF]
- permissions [WPF], detecting
- feature security requirements [WPF]
- managing permissions [WPF]
ms.assetid: ef2c0810-1dbf-4511-babd-1fab95b523b5
ms.openlocfilehash: 259db84c8ab3b9bbad809b9636ba18537dd6fe62
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400725"
---
# <a name="wpf-partial-trust-security"></a>Segurança parcialmente confiável do WPF
<a name="introduction"></a> Em geral, os aplicativos da Internet devem ter acesso restrito aos recursos críticos do sistema, para evitar danos mal-intencionados. Por padrão, [!INCLUDE[TLA#tla_html](../../../includes/tlasharptla-html-md.md)] e as linguagens de script do lado do cliente não são capazes de acessar recursos críticos do sistema. Como os aplicativos hospedados no navegador Windows Presentation Foundation (WPF) podem ser iniciados no navegador, eles devem estar em conformidade com um conjunto semelhante de restrições. Para impor essas restrições, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] baseia-se na CAS (segurança de acesso do código) e no ClickOnce (consulte [estratégia de segurança do WPF – segurança da plataforma](wpf-security-strategy-platform-security.md)). Por padrão, aplicativos hospedados em navegador solicitam o conjunto de permissões de CAS de zona da Internet, independentemente de serem iniciados da Internet, da intranet local ou do computador local. Aplicativos que são executados com nada menos do que o conjunto completo de permissões devem ser executados com confiança parcial.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]fornece uma ampla variedade de suporte para garantir que a maior funcionalidade possível possa ser usada com segurança em confiança parcial e, juntamente com o CAS, fornece suporte adicional para programação de confiança parcial.  
  
 Esse tópico contém as seguintes seções:  
  
- [Segurança parcialmente confiável do recurso de WPF](#WPF_Feature_Partial_Trust_Support)  
  
- [Programação de confiança parcial](#Partial_Trust_Programming)  
  
- [Gerenciando permissões](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## <a name="wpf-feature-partial-trust-support"></a>Segurança parcialmente confiável do recurso de WPF  
 A tabela a seguir lista os recursos de alto nível do Windows Presentation Foundation (WPF) que são seguros para usar dentro dos limites do conjunto de permissões de zona da Internet.  
  
 Tabela 1: Recursos do WPF que são seguros em confiança parcial  
  
|Área de recursos|Recurso|  
|------------------|-------------|  
|Geral|Janela do Navegador<br /><br /> Local do acesso de origem<br /><br /> IsolatedStorage (limite de 512KB)<br /><br /> Provedores de UIAutomation<br /><br /> Comando<br /><br /> IMEs (Editores de Método de Entrada)<br /><br /> Tinta e caneta eletrônica<br /><br /> Simulação de arrastar/soltar usando eventos de movimento e captura do Mouse<br /><br /> OpenFileDialog<br /><br /> Desserialização de XAML (via XamlReader)|  
|Integração da Web|Caixa de diálogo de download do Navegador<br /><br /> Navegação iniciada pelo usuário de nível superior<br /><br /> mailto:links<br /><br /> Parâmetros do Uniform Resource Identifier<br /><br /> HTTPWebRequest<br /><br /> Conteúdo do WPF hospedado em um IFRAME<br /><br /> Hospedagem de páginas do mesmo Site HTML usando o quadro<br /><br /> Hospedagem de páginas do mesmo Site HTML usando o navegador da Web<br /><br /> Serviços Web (ASMX)<br /><br /> Serviços Web (usando o Windows Communication Foundation)<br /><br /> Script<br /><br /> Document Object Model|  
|Visuais|2D e 3D<br /><br /> Animação<br /><br /> Mídia (Site de origem e entre domínios)<br /><br /> Geração de imagens/áudio/vídeo|  
|Leitura|FlowDocuments<br /><br /> Documentos XPS<br /><br /> Fontes internas e do sistema<br /><br /> Fontes CFF e TrueType|  
|Edição|Verificação de ortografia<br /><br /> RichTextBox<br /><br /> Texto sem formatação e suporte à área de transferência de tinta<br /><br /> Colar iniciado pelo usuário<br /><br /> Copiando conteúdo selecionado|  
|Controles|Controles gerais|  
  
 Esta tabela aborda os [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] recursos em um alto nível. Para obter informações mais detalhadas, [!INCLUDE[TLA#tla_lhsdk](../../../includes/tlasharptla-lhsdk-md.md)] o documenta as permissões exigidas por cada membro no [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Além disso, os recursos a seguir possuem informações mais detalhadas sobre a execução em confiança parcial, incluindo considerações especiais.  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)](consulte [visão geral de XAML (WPF)](./advanced/xaml-overview-wpf.md)).  
  
- Pop-ups ( <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>consulte).  
  
- Arrastar e soltar (consulte [visão geral de arrastar e soltar](./advanced/drag-and-drop-overview.md)).  
  
- Área de transferência <xref:System.Windows.Clipboard?displayProperty=nameWithType>(consulte).  
  
- Geração de imagens <xref:System.Windows.Controls.Image?displayProperty=nameWithType>(consulte).  
  
- Serialização (consulte <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>, <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>).  
  
- Caixa de diálogo abrir arquivo ( <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>consulte).  
  
 A tabela a seguir descreve os [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] recursos que não são seguros para serem executados dentro dos limites do conjunto de permissões de zona da Internet.  
  
 Tabela 2: Recursos do WPF que não são seguros em confiança parcial  
  
|Área de recursos|Recurso|  
|------------------|-------------|  
|Geral|Janela (Caixas de diálogo e janelas definidas pelo aplicativo)<br /><br /> SaveFileDialog<br /><br /> Sistema de arquivos<br /><br /> Acesso ao Registro<br /><br /> Arrastar e soltar<br /><br /> Serialização de XAML (via XamlWriter.Save)<br /><br /> Clientes de UIAutomation<br /><br /> Acesso à fonte de janela (HwndHost)<br /><br /> Suporte completo à fala<br /><br /> Interoperabilidade dos Windows Forms|  
|Visuais|Efeitos de bitmap<br /><br /> Codificação de imagem|  
|Edição|Área de transferência do formato Rich Text<br /><br /> Suporte completo para XAML|  
  
<a name="Partial_Trust_Programming"></a>   
## <a name="partial-trust-programming"></a>Programação de confiança parcial  
 Para [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] aplicativos, o código que excede o conjunto de permissões padrão terá um comportamento diferente, dependendo da zona de segurança. Em alguns casos, o usuário receberá um aviso ao tentar instalá-lo. O usuário pode optar por continuar ou cancelar a instalação. A tabela a seguir descreve o comportamento do aplicativo para cada zona de segurança e o que você precisa fazer para que o aplicativo receba confiança total.  
  
|Zona de segurança|Comportamento|Obtendo confiança total|  
|-------------------|--------------|------------------------|  
|Computador local|Confiança total automática|Nenhuma ação é necessária.|  
|Intranet e sites confiáveis|Aviso para confiança total|Assinar o XBAP com um certificado para que o usuário veja o código-fonte no aviso.|  
|Internet|Falha com "Confiança não concedida"|Assine XBAP com um certificado.|  
  
> [!NOTE]
>  O comportamento descrito na tabela anterior é de confiança total XBAPs que não seguem o modelo de implantação do ClickOnce confiáveis.  
  
 Em geral, o código que pode exceder as permissões permitidas é provavelmente código comum que é compartilhado entre autônomos e aplicativos hospedados pelo navegador. CAS e [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] oferecem várias técnicas para gerenciar esse cenário.  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### <a name="detecting-permissions-using-cas"></a>Detectando permissões usando o CAS  
 Em algumas situações, é possível que o código compartilhado em assemblies de biblioteca seja usado por aplicativos autônomos e [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]pelo. Nesses casos, código pode executar funcionalidades que podem exigir mais permissões do que o conjunto de permissões que o aplicativo permite. Seu aplicativo pode detectar se ele tem ou não uma determinada permissão usando a segurança do Microsoft .NET Framework. Especificamente, ele pode testar se ele tem uma permissão específica chamando o <xref:System.Security.CodeAccessPermission.Demand%2A> método na instância da permissão desejada. Isso é mostrado no exemplo a seguir, que tem código que consulta para que tenha a capacidade de salvar um arquivo no disco local:  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Se um aplicativo não tiver a permissão desejada, a chamada para <xref:System.Security.CodeAccessPermission.Demand%2A> emitirá uma exceção de segurança. Caso contrário, a permissão foi concedida. `IsPermissionGranted`encapsula esse comportamento e retorna `true` ou `false` conforme apropriado.  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### <a name="graceful-degradation-of-functionality"></a>Degradação gradual de funcionalidade  
 Ser capaz de detectar se o código tem permissão para fazer o que precisa fazer é interessante para o código que pode ser executado em diferentes regiões. Ao detectar a zona é uma coisa, que é muito melhor fornecer uma alternativa para o usuário, se possível. Por exemplo, um aplicativo de confiança total geralmente permite aos usuários criar arquivos em qualquer lugar que querem, embora um aplicativo parcialmente confiável só pode criar arquivos no armazenamento isolado. Se o código para criar um arquivo existe em um assembly que é compartilhado por aplicativos de confiança total (autônomo) e aplicativos de confiança parcial (online) e ambos os aplicativos deseja que os usuários criem arquivos, o código compartilhado deverá detectar se ele está em execução em confiança parcial ou total antes de criar um arquivo no local apropriado. O código a seguir demonstra a ambos.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 Em muitos casos, você deve ser capaz de encontrar uma alternativa de confiança parcial.  
  
 Em um ambiente controlado, como uma intranet, estruturas gerenciadas personalizadas podem ser instaladas na base do cliente no [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)]. Essas bibliotecas podem executar código que requer confiança total e são referenciadas de aplicativos que só têm permissão de confiança parcial usando <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (para obter mais informações, consulte [segurança](security-wpf.md) e [estratégia de segurança do WPF – segurança da plataforma](wpf-security-strategy-platform-security.md)).  
  
<a name="Browser_Host_Detection"></a>   
### <a name="browser-host-detection"></a>Detecção de Host do navegador  
 O uso de CAS para verificar permissões é uma técnica adequada quando você precisa verificar por permissão. No entanto, essa técnica depende capturar exceções como uma parte normal processamento, que não é recomendado em geral e pode ter problemas de desempenho. Em vez disso, [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] se o seu for executado apenas dentro da área restrita da zona <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> da Internet, você poderá usar [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)]a propriedade, que retorna true para.  
  
> [!NOTE]
>  <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A>distingue apenas se um aplicativo está em execução em um navegador, não em qual conjunto de permissões um aplicativo está sendo executado.  
  
<a name="Managing_Permissions"></a>   
## <a name="managing-permissions"></a>Gerenciando permissões  
 Por padrão, [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] execute com confiança parcial (conjunto de permissões de zona da Internet padrão). No entanto, dependendo dos requisitos do aplicativo, é possível alterar o conjunto de permissões padrão. Por exemplo, se um [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] for iniciado a partir de uma intranet local, ele poderá tirar proveito de um conjunto de permissões maior, que é mostrado na tabela a seguir.  
  
 Tabela 3: LocalIntranet e permissões da Internet  
  
|Permissão|Atributo|Intranet Local|Internet|  
|----------------|---------------|-------------------|--------------|  
|DNS|Acessar Servidores DNS|Sim|Não|  
|Variáveis de ambiente|Ler|Sim|Não|  
|Caixas de diálogo de arquivo|Abrir|Sim|Sim|  
|Caixas de diálogo de arquivo|Irrestrito|Sim|Não|  
|Armazenamentos isolado|Isolamento de assembly por usuário|Sim|Não|  
|Armazenamentos isolado|Isolamento desconhecido|Sim|Sim|  
|Armazenamentos isolado|Cota de usuário ilimitada|Sim|Não|  
|Mídia|Imagens, vídeo e áudio seguro|Sim|Sim|  
|Imprimindo|Impressão padrão|Sim|Não|  
|Imprimindo|Impressão segura|Sim|Sim|  
|Reflexão|Emitir|Sim|Não|  
|Segurança|Execução de código gerenciado|Sim|Sim|  
|Segurança|Declarar permissões concedidas|Sim|Não|  
|Interface do Usuário|Irrestrito|Sim|Não|  
|Interface do Usuário|Windows de nível de segurança superior|Sim|Sim|  
|Interface do Usuário|Área de transferência própria|Sim|Sim|  
|Navegador da Web|Navegação do quadro seguro para HTML|Sim|Sim|  
  
> [!NOTE]
>  Recortar e colar só é permitido em confiança parcial quando iniciada pelo usuário.  
  
 Se você precisar aumentar as permissões, você precisará alterar as configurações do projeto e o manifesto do aplicativo ClickOnce. Para obter mais informações, consulte [Visão geral de aplicativos de navegador XAML WPF](./app-development/wpf-xaml-browser-applications-overview.md). Os documentos a seguir também podem ser úteis.  
  
- [Mage.exe (Manifest Generation and Editing Tool)](../tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
- [MageUI.exe (Manifest Generation and Editing Tool, cliente gráfico)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
- [Protegendo aplicativos ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
 Se o [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] exigir confiança total, você poderá usar as mesmas ferramentas para aumentar as permissões solicitadas. Embora um [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] só receba confiança total se ele estiver instalado e iniciado a partir do computador local, da intranet ou de uma URL listada nos sites confiáveis ou permitidos do navegador. Se o aplicativo for instalado da intranet ou em um site confiável, o usuário receberá o prompt ClickOnce padrão notificando sobre as permissões com privilégios elevados. O usuário pode optar por continuar ou cancelar a instalação.  
  
 Como alternativa, você pode usar o modelo de implantação do ClickOnce confiáveis para implantação de confiança total de qualquer zona de segurança. Para obter mais informações, consulte Visão geral e [segurança](security-wpf.md)da [implantação de aplicativos confiáveis](/visualstudio/deployment/trusted-application-deployment-overview) .  
  
## <a name="see-also"></a>Consulte também

- [Segurança](security-wpf.md)
- [Estratégia de segurança do WPF – segurança da plataforma](wpf-security-strategy-platform-security.md)
- [Estratégia de segurança do WPF – Engenharia de segurança](wpf-security-strategy-security-engineering.md)
