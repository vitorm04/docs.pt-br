---
title: Segurança parcial da confiança
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
ms.openlocfilehash: 99c7d9cfae2b137053ca77d9e3d7055b4674ce5b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174570"
---
# <a name="wpf-partial-trust-security"></a>Segurança parcialmente confiável do WPF
<a name="introduction"></a> Em geral, os aplicativos da Internet devem ter acesso restrito aos recursos críticos do sistema, para evitar danos mal-intencionados. Por padrão, os idiomas de script do lado do HTML e do cliente não são capazes de acessar recursos críticos do sistema. Como os aplicativos hospedados no navegador do Windows Presentation Foundation (WPF) podem ser lançados a partir do navegador, eles devem estar em conformidade com um conjunto semelhante de restrições. Para impor essas restrições, o WPF conta tanto com o Cas (Code Access Security) quanto no ClickOnce (ver [WPF Security Strategy - Platform Security](wpf-security-strategy-platform-security.md)). Por padrão, os aplicativos hospedados no navegador solicitam o conjunto cas da zona da Internet, independentemente de serem lançados da Internet, da intranet local ou do computador local. Aplicativos que são executados com nada menos do que o conjunto completo de permissões devem ser executados com confiança parcial.  
  
 O WPF fornece uma grande variedade de suporte para garantir que o máximo de funcionalidade possível possa ser usado com segurança em confiança parcial e, juntamente com o CAS, forneça suporte adicional para programação de confiança parcial.  
  
 Este tópico contém as seguintes seções:  
  
- [Segurança parcialmente confiável do recurso de WPF](#WPF_Feature_Partial_Trust_Support)  
  
- [Programação de confiança parcial](#Partial_Trust_Programming)  
  
- [Gerenciando permissões](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>
## <a name="wpf-feature-partial-trust-support"></a>Segurança parcialmente confiável do recurso de WPF  
 A tabela a seguir lista os recursos de alto nível do Windows Presentation Foundation (WPF) que são seguros de usar dentro dos limites do conjunto de permissões da região da Internet.  
  
 Tabela 1: Recursos de WPF que são aceitos em confiança parcial  
  
|Área de recurso|Recurso|  
|------------------|-------------|  
|Geral|Janela do Navegador<br /><br /> Local do acesso de origem<br /><br /> IsolatedStorage (limite de 512KB)<br /><br /> Provedores de UIAutomation<br /><br /> Comando<br /><br /> IMEs (Editores de Método de Entrada)<br /><br /> Tinta e caneta eletrônica<br /><br /> Simulação de arrastar/soltar usando eventos de movimento e captura do Mouse<br /><br /> OpenFileDialog<br /><br /> Desserialização de XAML (via XamlReader)|  
|Integração da Web|Caixa de diálogo de download do Navegador<br /><br /> Navegação iniciada pelo usuário de nível superior<br /><br /> mailto:links<br /><br /> Parâmetros do Uniform Resource Identifier<br /><br /> HTTPWebRequest<br /><br /> Conteúdo do WPF hospedado em um IFRAME<br /><br /> Hospedagem de páginas do mesmo Site HTML usando o quadro<br /><br /> Hospedagem de páginas do mesmo Site HTML usando o navegador da Web<br /><br /> Serviços Web (ASMX)<br /><br /> Serviços Web (usando o Windows Communication Foundation)<br /><br /> Scripting<br /><br /> Document Object Model|  
|Visuais|2D e 3D<br /><br /> Animação<br /><br /> Mídia (Site de origem e entre domínios)<br /><br /> Geração de imagens/áudio/vídeo|  
|Leitura|FlowDocuments<br /><br /> Documentos XPS<br /><br /> Fontes internas e do sistema<br /><br /> Fontes CFF e TrueType|  
|Edição|Verificação de ortografia<br /><br /> RichTextBox<br /><br /> Texto sem formatação e suporte à área de transferência de tinta<br /><br /> Colar iniciado pelo usuário<br /><br /> Copiando conteúdo selecionado|  
|Controles|Controles gerais|  
  
 Esta tabela cobre os recursos do WPF em um nível alto. Para obter informações mais detalhadas, o Windows SDK documenta as permissões exigidas por cada membro no WPF. Além disso, os recursos a seguir possuem informações mais detalhadas sobre a execução em confiança parcial, incluindo considerações especiais.  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)](ver [Visão Geral XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)).  
  
- Popups (ver <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>).  
  
- Arrastar e soltar (ver [Visão geral de arrastar e soltar](./advanced/drag-and-drop-overview.md)).  
  
- Prancheta <xref:System.Windows.Clipboard?displayProperty=nameWithType>(ver ).  
  
- Imagem (ver <xref:System.Windows.Controls.Image?displayProperty=nameWithType>).  
  
- Serialização <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>(ver <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>, ).  
  
- Abrir caixa de <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>diálogo de arquivo (ver ).  
  
 A tabela a seguir descreve os recursos do WPF que não são seguros para serem executados dentro dos limites do conjunto de permissões da região da Internet.  
  
 Tabela 2: Recursos de WPF que não estão seguros em confiança parcial  
  
|Área de recurso|Recurso|  
|------------------|-------------|  
|Geral|Janela (Caixas de diálogo e janelas definidas pelo aplicativo)<br /><br /> SaveFileDialog<br /><br /> Sistema de Arquivos<br /><br /> Acesso ao Registro<br /><br /> Arrastar e soltar<br /><br /> Serialização de XAML (via XamlWriter.Save)<br /><br /> Clientes de UIAutomation<br /><br /> Acesso à fonte de janela (HwndHost)<br /><br /> Suporte completo à fala<br /><br /> Interoperabilidade dos Windows Forms|  
|Visuais|Efeitos de bitmap<br /><br /> Codificação de imagem|  
|Edição|Área de transferência do formato Rich Text<br /><br /> Suporte completo para XAML|  
  
<a name="Partial_Trust_Programming"></a>
## <a name="partial-trust-programming"></a>Programação de confiança parcial  
 Para aplicativos XBAP, o código que excede o conjunto de permissões padrão terá um comportamento diferente dependendo da zona de segurança. Em alguns casos, o usuário receberá um aviso ao tentar instalá-lo. O usuário pode optar por continuar ou cancelar a instalação. A tabela a seguir descreve o comportamento do aplicativo para cada zona de segurança e o que você precisa fazer para que o aplicativo receba confiança total.  
  
|Zona de segurança|Comportamento|Obtendo confiança total|  
|-------------------|--------------|------------------------|  
|Computador local|Confiança total automática|Nenhuma ação é necessária.|  
|Intranet e sites confiáveis|Aviso para confiança total|Assinar o XBAP com um certificado para que o usuário veja o código-fonte no aviso.|  
|Internet|Falha com "Confiança não concedida"|Assinar o XBAP com um certificado.|  
  
> [!NOTE]
> O comportamento descrito na tabela anterior é de confiança total XBAPs que não seguem o modelo de implantação do ClickOnce confiáveis.  
  
 Em geral, o código que pode exceder as permissões permitidas é provavelmente código comum que é compartilhado entre autônomos e aplicativos hospedados pelo navegador. Cas e WPF oferecem diversas técnicas para gerenciar esse cenário.  
  
<a name="Detecting_Permissions_using_CAS"></a>
### <a name="detecting-permissions-using-cas"></a>Detectando permissões usando o CAS  
 Em algumas situações, é possível que o código compartilhado em conjuntos de bibliotecas seja usado tanto por aplicativos independentes quanto por XBAPs. Nesses casos, código pode executar funcionalidades que podem exigir mais permissões do que o conjunto de permissões que o aplicativo permite. Seu aplicativo pode detectar se ele tem ou não uma certa permissão usando a segurança do Microsoft .NET Framework. Especificamente, ele pode testar se ele tem <xref:System.Security.CodeAccessPermission.Demand%2A> uma permissão específica, chamando o método na instância da permissão desejada. Isso é mostrado no exemplo a seguir, que tem código que consulta para que tenha a capacidade de salvar um arquivo no disco local:  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Se um aplicativo não tiver a permissão <xref:System.Security.CodeAccessPermission.Demand%2A> desejada, a chamada para lançar uma exceção de segurança. Caso contrário, a permissão foi concedida. `IsPermissionGranted`encapsula esse comportamento e `true` `false` retorna ou conforme apropriado.  
  
<a name="Graceful_Degradation_of_Functionality"></a>
### <a name="graceful-degradation-of-functionality"></a>Degradação gradual de funcionalidade  
 Ser capaz de detectar se o código tem permissão para fazer o que precisa fazer é interessante para o código que pode ser executado em diferentes regiões. Ao detectar a zona é uma coisa, que é muito melhor fornecer uma alternativa para o usuário, se possível. Por exemplo, um aplicativo de confiança total geralmente permite aos usuários criar arquivos em qualquer lugar que querem, embora um aplicativo parcialmente confiável só pode criar arquivos no armazenamento isolado. Se o código para criar um arquivo existe em um assembly que é compartilhado por aplicativos de confiança total (autônomo) e aplicativos de confiança parcial (online) e ambos os aplicativos deseja que os usuários criem arquivos, o código compartilhado deverá detectar se ele está em execução em confiança parcial ou total antes de criar um arquivo no local apropriado. O código a seguir demonstra a ambos.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 Em muitos casos, você deve ser capaz de encontrar uma alternativa de confiança parcial.  
  
 Em um ambiente controlado, como uma intranet, estruturas gerenciadas personalizadas podem ser instaladas em toda a base de clientes no cache de montagem global (GAC). Essas bibliotecas podem executar códigos que exigem total confiança e serem referenciados <xref:System.Security.AllowPartiallyTrustedCallersAttribute> a partir de aplicativos que só são permitidos confiança parcial usando (para obter mais informações, consulte [Security](security-wpf.md) and [WPF Security Strategy - Platform Security](wpf-security-strategy-platform-security.md)).  
  
<a name="Browser_Host_Detection"></a>
### <a name="browser-host-detection"></a>Detecção de Host do navegador  
 Usar o CAS para verificar permissões é uma técnica adequada quando você precisa verificar em uma base por permissão. No entanto, essa técnica depende capturar exceções como uma parte normal processamento, que não é recomendado em geral e pode ter problemas de desempenho. Em vez disso, se o aplicativo do navegador XAML (XBAP) for <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> executado apenas dentro da caixa de areia da zona da Internet, você poderá usar a propriedade, que retorna verdadeira para aplicativos de navegador XAML (XBAPs).  
  
> [!NOTE]
> <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A>só distingue se um aplicativo está sendo executado em um navegador, não com qual conjunto de permissões um aplicativo está sendo executado.  
  
<a name="Managing_Permissions"></a>
## <a name="managing-permissions"></a>Gerenciando permissões  
 Por padrão, os XBAPs são executados com confiança parcial (conjunto de permissões de região de Internet padrão). No entanto, dependendo dos requisitos do aplicativo, é possível alterar o conjunto de permissões padrão. Por exemplo, se um XBAPs for lançado a partir de uma intranet local, ele poderá aproveitar um conjunto de permissões aumentado, que é mostrado na tabela a seguir.  
  
 Tabela 3: Permissões de Intranet Local e de Internet  
  
|Permissão|Atributo|Intranet Local|Internet|  
|----------------|---------------|-------------------|--------------|  
|DNS|Acessar Servidores DNS|Sim|Não|  
|Variáveis de ambiente|Ler|Sim|Não|  
|Caixas de diálogo de arquivo|Aberto|Sim|Sim|  
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
> Recortar e colar só é permitido em confiança parcial quando iniciada pelo usuário.  
  
 Se você precisar aumentar as permissões, você precisará alterar as configurações do projeto e o manifesto do aplicativo ClickOnce. Para obter mais informações, consulte [visão geral dos aplicativos do navegador WPF XAML](./app-development/wpf-xaml-browser-applications-overview.md). Os documentos a seguir também podem ser úteis.  
  
- [Mage.exe (Ferramenta de Geração e Edição de Manifestos)](../tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
- [MageUI.exe (Ferramenta de Geração e Edição de Manifesto, Cliente Gráfico)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
- [Protegendo os aplicativos ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
 Se o seu XBAP exigir total confiança, você pode usar as mesmas ferramentas para aumentar as permissões solicitadas. Embora um XBAP só receba total confiança se for instalado e lançado a partir do computador local, a intranet ou de uma URL listada nos sites confiáveis ou permitidos do navegador. Se o aplicativo for instalado da intranet ou em um site confiável, o usuário receberá o prompt ClickOnce padrão notificando sobre as permissões com privilégios elevados. O usuário pode optar por continuar ou cancelar a instalação.  
  
 Como alternativa, você pode usar o modelo de implantação do ClickOnce confiáveis para implantação de confiança total de qualquer zona de segurança. Para obter mais informações, consulte Visão geral de [implantação de aplicativos confiáveis](/visualstudio/deployment/trusted-application-deployment-overview) e [segurança](security-wpf.md).  
  
## <a name="see-also"></a>Confira também

- [Segurança](security-wpf.md)
- [Estratégia de segurança do WPF - segurança da plataforma](wpf-security-strategy-platform-security.md)
- [Estratégia de segurança do WPF – Engenharia de segurança](wpf-security-strategy-security-engineering.md)
