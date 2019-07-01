---
title: Visão geral dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- smart clients
- Windows Forms, about Windows Forms
ms.assetid: 3a2b6284-c8d6-4e1c-8c69-0bed38f38cd4
ms.openlocfilehash: 71bf50bdcf058e94981dc5df4731b5d32dcc2069
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487200"
---
# <a name="windows-forms-overview"></a>Visão geral dos Windows Forms

A visão geral a seguir descreve as vantagens dos aplicativos cliente inteligentes, os principais recursos de programação dos Windows Forms e como você pode usar o Windows Forms para criar clientes inteligentes que atendem às necessidades de empresas e usuários finais de hoje.

## <a name="windows-forms-and-smart-client-apps"></a>Windows Forms e aplicativos de cliente inteligente

 Com o Windows Forms, você desenvolve clientes inteligentes. *Clientes inteligentes* são aplicativos graficamente ricos que são fáceis de implantar e atualizar, podem funcionar quando eles estão conectados ou desconectados da Internet e podem acessar recursos no computador local de maneira mais segura do que os aplicativos tradicionais baseados no Windows.

### <a name="build-rich-interactive-user-interfaces"></a>Criar interfaces do usuário ricas e interativas

 Windows Forms é uma tecnologia de cliente inteligente para o .NET Framework, um conjunto de bibliotecas gerenciadas que simplificam tarefas comuns de aplicativos como leitura e gravação para o sistema de arquivos. Quando você usa um ambiente de desenvolvimento como o Visual Studio, você pode criar aplicativos de cliente inteligente do Windows Forms que exibem informações, solicitam entrada de usuários e se comunicar com computadores remotos em uma rede.

 nos Windows Forms, um *formulário* é uma superfície visual na qual são exibidas informações para o usuário. Normalmente, os aplicativos dos Windows Forms são compilados com o acréscimo de controles a formulários e de respostas de desenvolvimento a ações do usuário, como cliques do mouse ou pressionamentos de teclas. Um *controle* é um elemento discreto de interface do usuário que exibe dados ou aceita a entrada de dados.

 Quando um usuário executa alguma ação em seu formulário ou em um de seus controles, a ação gera um evento. O seu aplicativo reage a esses eventos usando código e os processa quando eles acontecem. Para obter mais informações, consulte [Criando manipuladores de eventos nos Windows Forms](creating-event-handlers-in-windows-forms.md).

 O Windows Forms contém uma variedade de controles que podem ser adicionados aos formulários: controles que exibem caixas de texto, botões, caixas suspensas, botões de opção e até mesmo páginas da Web. Para obter uma lista de todos os controles que podem ser usados em um formulário, consulte [Controles que podem ser usados nos Windows Forms](./controls/controls-to-use-on-windows-forms.md). Se um controle existente não atender às suas necessidades, os formulários do Windows também oferece suporte à criação de seus próprios controles personalizados usando o <xref:System.Windows.Forms.UserControl> classe.

 O Windows Forms tem controles avançados de interface do usuário que emulam recursos em aplicativos de alta tecnologia, como o Microsoft Office. Quando você usa o <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.MenuStrip> controle, você pode criar barras de ferramentas e menus que contenham texto e imagens, exibem submenus e hospedam outros controles como caixas de texto e caixas de combinação.

 Com o arrastar e soltar **Designer de formulários do Windows** no Visual Studio, você pode criar facilmente aplicativos de formulários do Windows. Basta selecionar os controles com o seu cursor e adicioná-los no local do formulário desejado. O designer oferece ferramentas como linhas de grade e linhas de alinhamento para facilitar o alinhamento dos controles. E se você usa o Visual Studio ou compilar na linha de comando, você pode usar o <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> e <xref:System.Windows.Forms.SplitContainer> controles avançados de criar layouts de formulários em menos tempo.

 Por fim, se for necessário criar seus próprios elementos personalizados da interface do usuário, o <xref:System.Drawing> namespace contém uma grande seleção de classes para renderizar linhas, círculos e outras formas diretamente em um formulário.

> [!NOTE]
> Os controles dos Windows Forms não são projetados para a realização de marshaling entre domínios de aplicativo. Por esse motivo, a Microsoft não suporta passando um controle Windows Forms em um <xref:System.AppDomain> limite, mesmo que o <xref:System.Windows.Controls.Control> tipo de base de <xref:System.MarshalByRefObject> pareça indicar que isso é possível. Os aplicativos dos Windows Forms que têm vários domínios de aplicativo têm suporte, desde que nenhum controle dos Windows Forms seja passado entre limites de domínio de aplicativo.

#### <a name="create-forms-and-controls"></a>Criar formulários e controles

Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda.

|Descrição|Tópico da ajuda|
|-----------------|----------------|
|Usando controles em formulários|[Como: Adicionar controles ao Windows Forms](./controls/how-to-add-controls-to-windows-forms.md)|
|Usando o <xref:System.Windows.Forms.ToolStrip> controle|[Como: Criar um ToolStrip básico com itens padrão usando o Designer](./controls/create-a-basic-wf-toolstrip-with-standard-items-using-the-designer.md)|
|Criando gráficos com <xref:System.Drawing>|[Introdução à Programação de Elementos Gráficos](./advanced/getting-started-with-graphics-programming.md)|
|Criando controles personalizados|[Como: Herdar da classe UserControl](./controls/how-to-inherit-from-the-usercontrol-class.md)|

### <a name="display-and-manipulate-data"></a>Exibir e manipular dados
 Muitos aplicativos precisam exibir dados obtidos de um banco de dados, de um arquivo XML, de um serviço Web XML ou de outra fonte de dados. Windows Forms fornece um controle flexível chamado o <xref:System.Windows.Forms.DataGridView> controle para a exibição desses dados tabulares em um formato tradicional de linha e coluna, para que todos os dados ocupem suas próprias células. Quando você usa <xref:System.Windows.Forms.DataGridView>, você pode personalizar a aparência de células individuais, bloquear linhas arbitrárias e colunas de colocarem e exibem controles complexos em células, entre outros recursos.

 A conexão a fontes de dados pela rede é uma tarefa simples com clientes inteligentes dos Windows Forms. O <xref:System.Windows.Forms.BindingSource> componente representa uma conexão a uma fonte de dados e expõe métodos para associar dados a controles de navegação para registros anteriores e seguintes, edição de registros e salvar as alterações de volta para a fonte original. O <xref:System.Windows.Forms.BindingNavigator> controle fornece uma interface simple sobre o <xref:System.Windows.Forms.BindingSource> componente para que os usuários navegarem entre registros.

 É possível criar facilmente controles de associação de dados usando a janela Fontes de Dados. A janela exibe fontes de dados como bancos de dados, serviços Web e objetos em seu projeto. Você pode criar controles de associação de dados ao arrastar itens dessa janela para os formulários do seu projeto. Você também pode associar controles existentes a dados ao arrastar objetos da janela Fontes de Dados para eles.

 Outro tipo de vinculação de dados que você pode gerenciar nos Windows Forms é chamado de *configurações*. A maioria dos aplicativos de cliente inteligente deve manter algumas informações sobre seu estado de tempo de execução, como o último tamanho de formulário conhecido e reter dados de preferência do usuário, como os locais padrão para os arquivos salvos. O recurso de configuração de aplicativo lida com esses requisitos ao oferecer uma forma fácil de armazenar ambos os tipos de configuração no computador cliente. Depois de definir essas configurações usando o Visual Studio ou um editor de código, as configurações são mantidas como XML e automaticamente lidas para a memória em tempo de execução.

#### <a name="display-and-manipulate-data"></a>Exibir e manipular dados

Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda.

|Descrição|Tópico da ajuda|
|-----------------|----------------|
|Usando o <xref:System.Windows.Forms.BindingSource> componente|[Como: Associar controles dos Windows Forms com o componente BindingSource usando o Designer](./controls/bind-wf-controls-with-the-bindingsource.md)|
|Trabalhando com fontes de dados ADO.NET|[Como: Classificar e filtrar dados ADO.NET com o Windows Forms componente BindingSource](./controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|Usando a janela de Fontes de Dados|[Associando controles do Windows Forms a dados no Visual Studio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)|
|Usando configurações de aplicativo|[Como: Criar configurações de aplicativo](./advanced/how-to-create-application-settings.md)|

### <a name="deploy-apps-to-client-computers"></a>Implantar aplicativos em computadores cliente

Depois de escrever o seu aplicativo, você precisa enviá-lo para seus usuários para que eles possam instalá-lo e executá-lo em seus próprios computadores cliente. Quando você usa a tecnologia ClickOnce, você pode implantar seus aplicativos no Visual Studio usando apenas alguns cliques e fornecer aos usuários uma URL apontando para seu aplicativo na Web. ClickOnce gerencia todos os elementos e dependências em seu aplicativo e garante que o aplicativo está instalado corretamente no computador cliente.

Aplicativos ClickOnce podem ser configurados para executar apenas quando o usuário está conectado à rede, ou para execução online e offline. Quando você especifica que um aplicativo deve oferecer suporte a operação offline, o ClickOnce adiciona um link para seu aplicativo o usuário **iniciar** menu. O usuário pode, em seguida, abrir o aplicativo sem usar a URL.

Quando você atualiza o seu aplicativo, publica um novo manifesto de implantação e uma nova cópia do seu aplicativo em seu servidor Web. ClickOnce detecta que há uma atualização disponível e atualizar a instalação do usuário; nenhuma programação personalizada é necessária para a atualização de assemblies antigos.

#### <a name="deploy-clickonce-apps"></a>Implantar aplicativos ClickOnce

Para obter uma introdução completa ao ClickOnce, consulte [implantação e segurança do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Para informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda,

|Descrição|Tópico da ajuda|
|-----------------|----------------|
|Implantar um aplicativo usando o ClickOnce|[Como: Publicar um aplicativo ClickOnce usando o assistente de publicação](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Passo a passo: Como implantar manualmente aplicativos ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|
|Atualizar uma implantação do ClickOnce|[Como: Gerenciar atualizações para um aplicativo ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|
|Gerenciando a segurança com o ClickOnce|[Como: Habilitar configurações de segurança do ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|

### <a name="other-controls-and-features"></a>Outros controles e recursos

Existem muitos outros recursos dos Windows Forms que tornam as tarefas comuns de implementação mais fáceis e rápidas, como o suporte à criação de caixas de diálogo, impressão, adição da Ajuda e de documentação e localização do seu aplicativo para diversos idiomas. Além disso, Windows Forms se baseia no sistema de segurança robusto do .NET Framework. Com esse sistema, você pode liberar aplicativos mais seguros a seus clientes.

#### <a name="implement-other-controls-and-features"></a>Implementar outros controles e recursos

Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda.

|Descrição|Tópico da ajuda|
|-----------------|----------------|
|Imprimindo o conteúdo de um formulário|[Como: Imprimir elementos gráficos nos Windows Forms](./advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Como: Imprimir um arquivo de texto de várias páginas nos Windows Forms](./advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|
|Saiba mais sobre a segurança dos Windows Forms|[Visão geral da segurança dos Windows Forms](security-in-windows-forms-overview.md)|

## <a name="see-also"></a>Consulte também

- [Guia de introdução ao Windows Forms](getting-started-with-windows-forms.md)
- [Criando um novo Windows Form](creating-a-new-windows-form.md)
- [Visão geral do controle ToolStrip](./controls/toolstrip-control-overview-windows-forms.md)
- [Visão geral do controle DataGridView](./controls/datagridview-control-overview-windows-forms.md)
- [Visão geral do componente BindingSource](./controls/bindingsource-component-overview.md)
- [Visão Geral das Configurações do Aplicativo](./advanced/application-settings-overview.md)
- [Segurança e implantação do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
