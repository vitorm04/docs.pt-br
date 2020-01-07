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
ms.openlocfilehash: ce9341a45b43c4af4543cf473597c273c33701fc
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636543"
---
# <a name="wpf-partial-trust-security"></a>Segurança parcialmente confiável do WPF
<a name="introduction"></a> Em geral, os aplicativos da Internet devem ter acesso restrito aos recursos críticos do sistema, para evitar danos mal-intencionados. Por padrão, as linguagens de script HTML e do lado do cliente não são capazes de acessar recursos críticos do sistema. Como os aplicativos hospedados no navegador Windows Presentation Foundation (WPF) podem ser iniciados no navegador, eles devem estar em conformidade com um conjunto semelhante de restrições. Para impor essas restrições, o WPF conta com a CAS (segurança de acesso do código) e o ClickOnce (consulte [estratégia de segurança do WPF – segurança da plataforma](wpf-security-strategy-platform-security.md)). Por padrão, aplicativos hospedados em navegador solicitam o conjunto de permissões de CAS de zona da Internet, independentemente de serem iniciados da Internet, da intranet local ou do computador local. Aplicativos que são executados com nada menos do que o conjunto completo de permissões devem ser executados com confiança parcial.  
  
 O WPF fornece uma ampla variedade de suporte para garantir que a maior funcionalidade possível possa ser usada com segurança em confiança parcial e, juntamente com o CAS, fornece suporte adicional para programação de confiança parcial.  
  
 Esse tópico contém as seguintes seções:  
  
- [Segurança parcialmente confiável do recurso de WPF](#WPF_Feature_Partial_Trust_Support)  
  
- [Programação de confiança parcial](#Partial_Trust_Programming)  
  
- [Gerenciando permissões](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## <a name="wpf-feature-partial-trust-support"></a>Segurança parcialmente confiável do recurso de WPF  
 A tabela a seguir lista os recursos de alto nível do Windows Presentation Foundation (WPF) que são seguros para usar dentro dos limites do conjunto de permissões de zona da Internet.  
  
 Tabela 1: Recursos de WPF que são aceitos em confiança parcial  
  
|Área do recurso|Recurso|  
|------------------|-------------|  
|Geral|Janela do Navegador<br /><br /> Local do acesso de origem<br /><br /> IsolatedStorage (limite de 512KB)<br /><br /> Provedores de UIAutomation<br /><br /> Comando<br /><br /> IMEs (Editores de Método de Entrada)<br /><br /> Tinta e caneta eletrônica<br /><br /> Simulação de arrastar/soltar usando eventos de movimento e captura do Mouse<br /><br /> OpenFileDialog<br /><br /> Desserialização de XAML (via XamlReader)|  
|Integração da Web|Caixa de diálogo de download do Navegador<br /><br /> Navegação iniciada pelo usuário de nível superior<br /><br /> mailto:links<br /><br /> Parâmetros do Uniform Resource Identifier<br /><br /> HTTPWebRequest<br /><br /> Conteúdo do WPF hospedado em um IFRAME<br /><br /> Hospedagem de páginas do mesmo Site HTML usando o quadro<br /><br /> Hospedagem de páginas do mesmo Site HTML usando o navegador da Web<br /><br /> Serviços Web (ASMX)<br /><br /> Serviços Web (usando o Windows Communication Foundation)<br /><br /> {1&gt;Script&lt;1}<br /><br /> Document Object Model|  
|Visuais|2D e 3D<br /><br /> {1&gt;Animação&lt;1}<br /><br /> Mídia (Site de origem e entre domínios)<br /><br /> Geração de imagens/áudio/vídeo|  
|Lendo|FlowDocuments<br /><br /> Documentos XPS<br /><br /> Fontes internas e do sistema<br /><br /> Fontes CFF e TrueType|  
|Edição|Verificação de ortografia<br /><br /> RichTextBox<br /><br /> Texto sem formatação e suporte à área de transferência de tinta<br /><br /> Colar iniciado pelo usuário<br /><br /> Copiando conteúdo selecionado|  
|Controles|Controles gerais|  
  
 Esta tabela aborda os recursos do WPF em um alto nível. Para obter informações mais detalhadas, o SDK do Windows documenta as permissões exigidas por cada membro no WPF. Além disso, os recursos a seguir possuem informações mais detalhadas sobre a execução em confiança parcial, incluindo considerações especiais.  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] (consulte [visão geral do XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)).  
  
- Pop-ups (consulte <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>).  
  
- Arrastar e soltar (consulte [visão geral de arrastar e soltar](./advanced/drag-and-drop-overview.md)).  
  
- Área de transferência (consulte <xref:System.Windows.Clipboard?displayProperty=nameWithType>).  
  
- Geração de imagens (consulte <xref:System.Windows.Controls.Image?displayProperty=nameWithType>).  
  
- Serialização (consulte <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>, <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>).  
  
- Caixa de diálogo abrir arquivo (consulte <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>).  
  
 A tabela a seguir descreve os recursos do WPF que não são seguros para serem executados dentro dos limites do conjunto de permissões de zona da Internet.  
  
 Tabela 2: Recursos de WPF que não estão seguros em confiança parcial  
  
|Área do recurso|Recurso|  
|------------------|-------------|  
|Geral|Janela (Caixas de diálogo e janelas definidas pelo aplicativo)<br /><br /> SaveFileDialog<br /><br /> Sistema de arquivos<br /><br /> Acesso ao Registro<br /><br /> Arrastar e soltar<br /><br /> Serialização de XAML (via XamlWriter.Save)<br /><br /> Clientes de UIAutomation<br /><br /> Acesso à fonte de janela (HwndHost)<br /><br /> Suporte completo à fala<br /><br /> Interoperabilidade dos Windows Forms|  
|Visuais|Efeitos de bitmap<br /><br /> Codificação de imagem|  
|Edição|Área de transferência do formato Rich Text<br /><br /> Suporte completo para XAML|  
  
<a name="Partial_Trust_Programming"></a>   
## <a name="partial-trust-programming"></a>Programação de confiança parcial  
 Para aplicativos XBAP, o código que excede o conjunto de permissões padrão terá um comportamento diferente, dependendo da zona de segurança. Em alguns casos, o usuário receberá um aviso ao tentar instalá-lo. O usuário pode optar por continuar ou cancelar a instalação. A tabela a seguir descreve o comportamento do aplicativo para cada zona de segurança e o que você precisa fazer para que o aplicativo receba confiança total.  
  
|Zona de segurança|Comportamento|Obtendo confiança total|  
|-------------------|--------------|------------------------|  
|Computador local|Confiança total automática|Nenhuma ação é necessária.|  
|Intranet e sites confiáveis|Aviso para confiança total|Assinar o XBAP com um certificado para que o usuário veja o código-fonte no aviso.|  
|Internet|Falha com "Confiança não concedida"|Assinar o XBAP com um certificado.|  
  
> [!NOTE]
> O comportamento descrito na tabela anterior é de confiança total XBAPs que não seguem o modelo de implantação do ClickOnce confiáveis.  
  
 Em geral, o código que pode exceder as permissões permitidas é provavelmente código comum que é compartilhado entre autônomos e aplicativos hospedados pelo navegador. O CAS e o WPF oferecem várias técnicas para gerenciar esse cenário.  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### <a name="detecting-permissions-using-cas"></a>Detectando permissões usando o CAS  
 Em algumas situações, é possível que o código compartilhado em assemblies de biblioteca seja usado por aplicativos autônomos e XBAPs. Nesses casos, código pode executar funcionalidades que podem exigir mais permissões do que o conjunto de permissões que o aplicativo permite. Seu aplicativo pode detectar se ele tem ou não uma determinada permissão usando a segurança do Microsoft .NET Framework. Especificamente, ele pode testar se ele tem uma permissão específica chamando o método <xref:System.Security.CodeAccessPermission.Demand%2A> na instância da permissão desejada. Isso é mostrado no exemplo a seguir, que tem código que consulta para que tenha a capacidade de salvar um arquivo no disco local:  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Se um aplicativo não tiver a permissão desejada, a chamada para <xref:System.Security.CodeAccessPermission.Demand%2A> gerará uma exceção de segurança. Caso contrário, a permissão foi concedida. `IsPermissionGranted` encapsula esse comportamento e retorna `true` ou `false` conforme apropriado.  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### <a name="graceful-degradation-of-functionality"></a>Degradação gradual de funcionalidade  
 Ser capaz de detectar se o código tem permissão para fazer o que precisa fazer é interessante para o código que pode ser executado em diferentes regiões. Ao detectar a zona é uma coisa, que é muito melhor fornecer uma alternativa para o usuário, se possível. Por exemplo, um aplicativo de confiança total geralmente permite aos usuários criar arquivos em qualquer lugar que querem, embora um aplicativo parcialmente confiável só pode criar arquivos no armazenamento isolado. Se o código para criar um arquivo existe em um assembly que é compartilhado por aplicativos de confiança total (autônomo) e aplicativos de confiança parcial (online) e ambos os aplicativos deseja que os usuários criem arquivos, o código compartilhado deverá detectar se ele está em execução em confiança parcial ou total antes de criar um arquivo no local apropriado. O código a seguir demonstra a ambos.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 Em muitos casos, você deve ser capaz de encontrar uma alternativa de confiança parcial.  
  
 Em um ambiente controlado, como uma intranet, estruturas gerenciadas personalizadas podem ser instaladas na base do cliente no GAC (cache de assembly global). Essas bibliotecas podem executar código que requer confiança total e são referenciadas de aplicativos que só têm permissão de confiança parcial usando <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (para obter mais informações, consulte [segurança](security-wpf.md) e [estratégia de segurança do WPF – segurança da plataforma](wpf-security-strategy-platform-security.md)).  
  
<a name="Browser_Host_Detection"></a>   
### <a name="browser-host-detection"></a>Detecção de Host do navegador  
 O uso de CAS para verificar permissões é uma técnica adequada quando você precisa verificar por permissão. No entanto, essa técnica depende capturar exceções como uma parte normal processamento, que não é recomendado em geral e pode ter problemas de desempenho. Em vez disso, se o seu aplicativo de navegador XAML (XBAP) for executado somente dentro da área restrita da zona da Internet, você poderá usar a propriedade <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType>, que retorna true para aplicativos de navegador XAML (XBAPs).  
  
> [!NOTE]
> <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A> distingue apenas se um aplicativo está em execução em um navegador, e não em qual conjunto de permissões um aplicativo está sendo executado.  
  
<a name="Managing_Permissions"></a>   
## <a name="managing-permissions"></a>Gerenciando permissões  
 Por padrão, XBAPs são executados com confiança parcial (conjunto de permissões de zona da Internet padrão). No entanto, dependendo dos requisitos do aplicativo, é possível alterar o conjunto de permissões padrão. Por exemplo, se um XBAPs for iniciado a partir de uma intranet local, ele poderá tirar proveito de um conjunto de permissões maior, que é mostrado na tabela a seguir.  
  
 Tabela 3: Permissões de Intranet Local e de Internet  
  
|Permissão|Atributo|Intranet Local|Internet|  
|----------------|---------------|-------------------|--------------|  
|DNS|Acessar Servidores DNS|Sim|Não|  
|Variáveis de ambiente|Ler|Sim|Não|  
|Caixas de diálogo de arquivo|Open|Sim|Sim|  
|Caixas de diálogo de arquivo|Irrestrito|Sim|Não|  
|Armazenamentos isolado|Isolamento de assembly por usuário|Sim|Não|  
|Armazenamentos isolado|Isolamento desconhecido|Sim|Sim|  
|Armazenamentos isolado|Cota de usuário ilimitada|Sim|Não|  
|Mídia|Imagens, vídeo e áudio seguro|Sim|Sim|  
|Impressão|Impressão padrão|Sim|Não|  
|Impressão|Impressão segura|Sim|Sim|  
|Reflexão|Emitir|Sim|Não|  
|Segurança|Execução de código gerenciado|Sim|Sim|  
|Segurança|Declarar permissões concedidas|Sim|Não|  
|Interface do Usuário|Irrestrito|Sim|Não|  
|Interface do Usuário|Windows de nível de segurança superior|Sim|Sim|  
|Interface do Usuário|Área de transferência própria|Sim|Sim|  
|Navegador da Web|Navegação do quadro seguro para HTML|Sim|Sim|  
  
> [!NOTE]
> Recortar e colar só é permitido em confiança parcial quando iniciada pelo usuário.  
  
 Se você precisar aumentar as permissões, você precisará alterar as configurações do projeto e o manifesto do aplicativo ClickOnce. Para obter mais informações, consulte [Visão geral de aplicativos de navegador XAML WPF](./app-development/wpf-xaml-browser-applications-overview.md). Os documentos a seguir também podem ser úteis.  
  
- [Mage.exe (Manifest Generation and Editing Tool)](../tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
- [MageUI.exe (Manifest Generation and Editing Tool, cliente gráfico)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
- [Protegendo aplicativos ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
 Se o XBAP exigir confiança total, você poderá usar as mesmas ferramentas para aumentar as permissões solicitadas. Embora um XBAP só receba confiança total se ele estiver instalado e iniciado a partir do computador local, da intranet ou de uma URL listada nos sites confiáveis ou permitidos do navegador. Se o aplicativo for instalado da intranet ou em um site confiável, o usuário receberá o prompt ClickOnce padrão notificando sobre as permissões com privilégios elevados. O usuário pode optar por continuar ou cancelar a instalação.  
  
 Como alternativa, você pode usar o modelo de implantação do ClickOnce confiáveis para implantação de confiança total de qualquer zona de segurança. Para obter mais informações, consulte Visão geral e [segurança](security-wpf.md)da [implantação de aplicativos confiáveis](/visualstudio/deployment/trusted-application-deployment-overview) .  
  
## <a name="see-also"></a>Veja também

- [Security](security-wpf.md)
- [Estratégia de segurança do WPF – segurança da plataforma](wpf-security-strategy-platform-security.md)
- [Estratégia de segurança do WPF – Engenharia de segurança](wpf-security-strategy-security-engineering.md)
