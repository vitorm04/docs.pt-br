---
title: Visão geral dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- smart clients
- Windows Forms, about Windows Forms
ms.assetid: 3a2b6284-c8d6-4e1c-8c69-0bed38f38cd4
ms.openlocfilehash: 897d6fb8e0a150cc7fa498bb904b10d89ece9943
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486229"
---
# <a name="windows-forms-overview"></a>Visão geral dos Windows Forms
A visão geral a seguir descreve as vantagens dos aplicativos cliente inteligentes, os principais recursos de programação dos Windows Forms e como você pode usar o Windows Forms para criar clientes inteligentes que atendem às necessidades de empresas e usuários finais de hoje.  
  
## <a name="windows-forms-and-smart-client-applications"></a>Windows Forms e Smart Client Applications  
 Com o Windows Forms, você desenvolve clientes inteligentes. *Clientes inteligentes* são aplicativos graficamente ricos que são fáceis de implantar e atualizar, podem funcionar quando eles estão conectados ou desconectados da Internet e podem acessar recursos no computador local de maneira mais segura do que os aplicativos tradicionais baseados no Windows.  
  
### <a name="building-rich-interactive-user-interfaces"></a>Compilando interfaces do usuário sofisticadas e interativas  
 O Windows Forms é uma tecnologia de cliente inteligente para o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], um conjunto de bibliotecas gerenciadas que simplificam tarefas comuns de aplicativos como leitura e gravação para o sistema de arquivos. Quando você usa um ambiente de desenvolvimento como o Visual Studio, você pode criar aplicativos de cliente inteligente do Windows Forms que exibem informações, solicitam entrada de usuários e se comunicar com computadores remotos em uma rede.  
  
 nos Windows Forms, um *formulário* é uma superfície visual na qual são exibidas informações para o usuário. Normalmente, os aplicativos dos Windows Forms são compilados com o acréscimo de controles a formulários e de respostas de desenvolvimento a ações do usuário, como cliques do mouse ou pressionamentos de teclas. Um *controle* é um elemento discreto de interface do usuário que exibe dados ou aceita a entrada de dados.  
  
 Quando um usuário executa alguma ação em seu formulário ou em um de seus controles, a ação gera um evento. O seu aplicativo reage a esses eventos usando código e os processa quando eles acontecem. Para obter mais informações, consulte [Criando manipuladores de eventos nos Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
 O Windows Forms contém uma variedade de controles que podem ser adicionados aos formulários: controles que exibem caixas de texto, botões, caixas suspensas, botões de opção e até mesmo páginas da Web. Para obter uma lista de todos os controles que podem ser usados em um formulário, consulte [Controles que podem ser usados nos Windows Forms](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md). Se um controle existente não atender às suas necessidades, os formulários do Windows também oferece suporte à criação de seus próprios controles personalizados usando o <xref:System.Windows.Forms.UserControl> classe.  
  
 O Windows Forms tem controles avançados de interface do usuário que emulam recursos em aplicativos de alta tecnologia, como o Microsoft Office. Quando você usa o <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.MenuStrip> controle, você pode criar barras de ferramentas e menus que contenham texto e imagens, exibem submenus e hospedam outros controles como caixas de texto e caixas de combinação.  
  
 Com o Designer de formulários do Windows do Visual Studio arrastar e soltar, você pode criar facilmente aplicativos de formulários do Windows. Basta selecionar os controles com o seu cursor e adicioná-los no local do formulário desejado. O designer oferece ferramentas como linhas de grade e linhas de alinhamento para facilitar o alinhamento dos controles. E se você usa o Visual Studio ou compilar na linha de comando, você pode usar o <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> e <xref:System.Windows.Forms.SplitContainer> controles avançados de criar layouts de formulários em menos tempo.  
  
 Por fim, se for necessário criar seus próprios elementos personalizados da interface do usuário, o <xref:System.Drawing> namespace contém uma grande seleção de classes para renderizar linhas, círculos e outras formas diretamente em um formulário.  
  
> [!NOTE]
>  Os controles dos Windows Forms não são projetados para a realização de marshaling entre domínios de aplicativo. Por esse motivo, a Microsoft não suporta passando um controle Windows Forms em um <xref:System.AppDomain> limite, mesmo que o <xref:System.Windows.Controls.Control> tipo de base de <xref:System.MarshalByRefObject> pareça indicar que isso é possível. Os aplicativos dos Windows Forms que têm vários domínios de aplicativo têm suporte, desde que nenhum controle dos Windows Forms seja passado entre limites de domínio de aplicativo.  
  
#### <a name="help-creating-forms-and-controls"></a>Ajuda para criar formulários e controles  
 Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda.  
  
|Descrição|Tópico da ajuda|  
|-----------------|----------------|  
|Usando controles em formulários|[Como Adicionar Controles ao Windows Forms](../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|  
|Usando o <xref:System.Windows.Forms.ToolStrip> controle|[Como criar um ToolStrip básico com itens padrão usando o designer](../../../docs/framework/winforms/controls/create-a-basic-wf-toolstrip-with-standard-items-using-the-designer.md)|  
|Criando gráficos com <xref:System.Drawing>|[Introdução à Programação de Elementos Gráficos](../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|Criando controles personalizados|[Como herdar da classe UserControl](../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
### <a name="displaying-and-manipulating-data"></a>Exibindo e manipulando dados  
 Muitos aplicativos precisam exibir dados obtidos de um banco de dados, de um arquivo XML, de um serviço Web XML ou de outra fonte de dados. Windows Forms fornece um controle flexível chamado o <xref:System.Windows.Forms.DataGridView> controle para a exibição desses dados tabulares em um formato tradicional de linha e coluna, para que todos os dados ocupem suas próprias células. Quando você usa <xref:System.Windows.Forms.DataGridView>, você pode personalizar a aparência de células individuais, bloquear linhas arbitrárias e colunas de colocarem e exibem controles complexos em células, entre outros recursos.  
  
 A conexão a fontes de dados pela rede é uma tarefa simples com clientes inteligentes dos Windows Forms. O <xref:System.Windows.Forms.BindingSource> componente novo com o Windows Forms no [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] e o [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)], representa uma conexão a uma fonte de dados e expõe métodos para vinculação de dados a controles de navegação para registros anteriores e seguintes, edição de registros e salvar alterações de volta para a fonte original. O <xref:System.Windows.Forms.BindingNavigator> controle fornece uma interface simple sobre o <xref:System.Windows.Forms.BindingSource> componente para que os usuários navegarem entre registros.  
  
 É possível criar facilmente controles de associação de dados usando a janela Fontes de Dados. A janela exibe fontes de dados como bancos de dados, serviços Web e objetos em seu projeto. Você pode criar controles de associação de dados ao arrastar itens dessa janela para os formulários do seu projeto. Você também pode associar controles existentes a dados ao arrastar objetos da janela Fontes de Dados para eles.  
  
 Outro tipo de vinculação de dados que você pode gerenciar nos Windows Forms é chamado de *configurações*. A maioria dos aplicativos de cliente inteligente deve manter algumas informações sobre seu estado de tempo de execução, como o último tamanho de formulário conhecido e reter dados de preferência do usuário, como os locais padrão para os arquivos salvos. O recurso de configuração de aplicativo lida com esses requisitos ao oferecer uma forma fácil de armazenar ambos os tipos de configuração no computador cliente. Depois de definir essas configurações usando o Visual Studio ou um editor de código, as configurações são mantidas como XML e automaticamente lidas para a memória em tempo de execução.  
  
#### <a name="help-displaying-and-manipulating-data"></a>Ajuda para exibir e manipular dados  
 Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda.  
  
|Descrição|Tópico da ajuda|  
|-----------------|----------------|  
|Usando o <xref:System.Windows.Forms.BindingSource> componente|[Como associar controles dos Windows Forms ao componente BindingSource usando o designer](../../../docs/framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|Trabalhando com fontes de dados [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]|[Como classificar e filtrar dados ADO.NET com o componente BindingSource dos Windows Forms](../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|  
|Usando a janela de Fontes de Dados|[Passo a passo: exibindo dados em um Windows Form](https://msdn.microsoft.com/library/f6e08c2c-c792-43de-adf3-3e52c0100225)|  
|Usando configurações de aplicativo|[Como criar configurações de aplicativo](../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)|  
  
### <a name="deploying-applications-to-client-computers"></a>Implantando aplicativos em computadores cliente  
 Depois de escrever o seu aplicativo, você precisa enviá-lo para seus usuários para que eles possam instalá-lo e executá-lo em seus próprios computadores cliente. Quando você usa o [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] tecnologia, você pode implantar seus aplicativos no Visual Studio usando apenas alguns cliques e fornecer aos usuários uma URL apontando para seu aplicativo na Web. O [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] gerencia todos os elementos e as dependências do seu aplicativo e garante que ele seja instalado adequadamente no computador cliente.  
  
 Os aplicativos [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] podem ser configurados para serem executados somente quando o usuário estiver conectado à rede ou para execução online e offline. Quando você especifica que um aplicativo deve dar suporte à operação offline, o [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] adiciona um link ao seu aplicativo no menu **Iniciar** do usuário. O usuário pode, em seguida, abrir o aplicativo sem usar a URL.  
  
 Quando você atualiza o seu aplicativo, publica um novo manifesto de implantação e uma nova cópia do seu aplicativo em seu servidor Web. O [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] detecta que há uma atualização disponível e atualiza a instalação do usuário. Não é necessário haver uma programação personalizada para a atualização de assemblies antigos.  
  
#### <a name="help-deploying-clickonce-applications"></a>Ajuda para implantar aplicativos ClickOnce  
 Para obter uma introdução completa [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], consulte [Implantação e segurança do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Para informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda,  
  
|Descrição|Tópico da ajuda|  
|-----------------|----------------|  
|Implantando um aplicativo usando [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]|[Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Passo a passo: implantando um aplicativo ClickOnce manualmente](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Atualizando uma implantação [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]|[Como gerenciar atualizações para um aplicativo ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|Gerenciando a segurança com [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]|[Como habilitar configurações de segurança do ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
### <a name="other-controls-and-features"></a>Outros controles e recursos  
 Existem muitos outros recursos dos Windows Forms que tornam as tarefas comuns de implementação mais fáceis e rápidas, como o suporte à criação de caixas de diálogo, impressão, adição da Ajuda e de documentação e localização do seu aplicativo para diversos idiomas. Além disso, o Windows Forms depende do sistema de segurança robusto do [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Com esse sistema, você pode liberar aplicativos mais seguros a seus clientes.  
  
#### <a name="help-implementing-other-controls-and-features"></a>Ajuda para implementar outros controles e recursos  
 Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda.  
  
|Descrição|Tópico da ajuda|  
|-----------------|----------------|  
|Imprimindo o conteúdo de um formulário|[Como Imprimir Elementos Gráficos nos Windows Forms](../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Como Imprimir um Arquivo de Texto de Várias Páginas nos Windows Forms](../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|  
|Saiba mais sobre a segurança dos Windows Forms|[Visão geral da segurança dos Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)|  
  
## <a name="see-also"></a>Consulte também  
 [Guia de introdução ao Windows Forms](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [Criando um novo Windows Form](../../../docs/framework/winforms/creating-a-new-windows-form.md)  
 [Visão geral do controle ToolStrip](../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Visão geral do controle DataGridView](../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [Visão geral do componente BindingSource](../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 [Visão Geral das Configurações do Aplicativo](../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [Segurança e implantação do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
