---
title: Noções básicas de Aplicativo do Windows Forms (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
ms.openlocfilehash: dd3385d6459199d56f74abfb1b8e0e218a2adf78
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487797"
---
# <a name="windows-forms-application-basics-visual-basic"></a>Noções básicas de Aplicativo do Windows Forms (Visual Basic)
Uma parte importante do Visual Basic é a capacidade de criar aplicativos Windows Forms executados localmente nos computadores dos usuários. Você pode usar o Visual Studio para criar o aplicativo e interface do usuário usando Windows Forms. Um aplicativo Windows Forms se baseia nas classes do <xref:System.Windows.Forms> namespace.  
  
## <a name="designing-windows-forms-applications"></a>Aplicativos de formulários do Windows de criação  
 Você pode criar formulários do Windows e aplicativos de serviço do Windows com o Visual Studio. Para mais informações, consulte os seguintes tópicos:  
  
- [Introdução ao Windows Forms](../../../framework/winforms/getting-started-with-windows-forms.md). Fornece informações sobre como criar e programar Windows Forms.  
   
- [Controles do Windows Forms](../../../framework/winforms/controls/index.md). Coleção de tópicos que detalha o uso de controles de formulários do Windows.  
  
- [Aplicativos de serviço do Windows](../../../framework/windows-services/index.md). Lista os tópicos que explicam como criar serviços do Windows.  
  
## <a name="building-rich-interactive-user-interfaces"></a>Compilando interfaces do usuário sofisticadas e interativas  
 Windows Forms é o componente de cliente inteligente do .NET Framework, um conjunto de bibliotecas gerenciadas que habilita tarefas comuns de aplicativos como leitura e gravação para o sistema de arquivos. Usando um ambiente de desenvolvimento como o Visual Studio, você pode criar aplicativos do Windows Forms que exibem informações, solicitam entrada de usuários e se comunicar com computadores remotos em uma rede.  
  
 No Windows Forms, um formulário é uma superfície visual na qual são exibidas informações para o usuário. Normalmente, você criar aplicativos do Windows Forms colocando controles em formulários e respostas de desenvolvimento a ações do usuário, como cliques do mouse ou pressionamentos de teclas. Um *controle* é um elemento discreto de interface do usuário que exibe dados ou aceita a entrada de dados.  
  
### <a name="events"></a>Eventos  
 Quando um usuário faz algo em seu formulário ou um de seus controles, ele gera um evento. O seu aplicativo reage a esses eventos usando código e os processa quando eles acontecem. Para obter mais informações, consulte [Criando manipuladores de eventos nos Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
### <a name="controls"></a>Controles  
 Windows Forms contém uma variedade de controles que podem ser colocados em formulários: controles que exibem caixas de texto, botões, caixas suspensas, botões de opção e até mesmo páginas da Web. Para obter uma lista de todos os controles que podem ser usados em um formulário, consulte [Controles que podem ser usados nos Windows Forms](../../../framework/winforms/controls/controls-to-use-on-windows-forms.md). Se um controle existente não atender às suas necessidades, os formulários do Windows também oferece suporte à criação de seus próprios controles personalizados usando o <xref:System.Windows.Forms.UserControl> classe.  
  
 O Windows Forms tem controles avançados de interface do usuário que emulam recursos em aplicativos de alta tecnologia, como o Microsoft Office. Usando o <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.MenuStrip> controle, você pode criar barras de ferramentas e menus que contenham texto e imagens, exibem submenus e hospedam outros controles como caixas de texto e caixas de combinação.  
  
 Com o designer de formulários de arrastar e soltar do Visual Studio, você pode facilmente criar aplicativos do Windows Forms: basta selecionar os controles com o seu cursor e colocá-los onde você deseja no formulário. O designer oferece ferramentas como linhas de grade e "linhas de alinhamento" para facilitar o alinhamento dos controles. E se você usa o Visual Studio ou compilar na linha de comando, você pode usar o <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> e <xref:System.Windows.Forms.SplitContainer> controles avançados de criar layouts de formulários com mínimo de tempo e esforço.  
  
### <a name="custom-ui-elements"></a>Elementos de interface do usuário personalizada  
 Por fim, se for necessário criar seus próprios elementos personalizados da interface do usuário, o <xref:System.Drawing> namespace contém todas as classes necessárias para processar linhas, círculos e outras formas diretamente em um formulário.  
  
 Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda.  
  
|Para|Consulte|  
|--------|---------|  
|Criar um novo aplicativo Windows Forms com Visual Studio|[Tutorial 1: Criar um visualizador de imagens](/visualstudio/ide/tutorial-1-create-a-picture-viewer)|  
|Usar controles em formulários|[Como: Adicionar controles ao Windows Forms](../../../framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|   
|Criar gráficos com <xref:System.Drawing>|[Introdução à Programação de Elementos Gráficos](../../../framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|Criar controles personalizados|[Como: Herdar da classe UserControl](../../../framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
## <a name="displaying-and-manipulating-data"></a>Exibindo e manipulando dados  
 Muitos aplicativos precisam exibir dados obtidos de um banco de dados, de um arquivo XML, de um serviço Web XML ou de outra fonte de dados. Windows Forms fornece um controle flexível, chamado de <xref:System.Windows.Forms.DataGridView> para o processamento desses dados tabulares em um formato tradicional de linha e coluna, para que todos os dados ocupem suas próprias células. Usando <xref:System.Windows.Forms.DataGridView> você pode personalizar a aparência de células individuais, bloquear linhas e colunas em vigor arbitrárias e exibir controles complexos em células, entre outros recursos.  
  
 A conexão a fontes de dados pela rede é uma tarefa simples com clientes inteligentes dos Windows Forms. O <xref:System.Windows.Forms.BindingSource> componente novo com o Windows Forms no Visual Studio 2005 e o .NET Framework 2.0, representa uma conexão a uma fonte de dados e expõe métodos para associar dados a controles de navegação para registros anteriores e seguintes, edição de registros, e Salvando alterações de volta para a fonte original. O <xref:System.Windows.Forms.BindingNavigator> controle fornece uma interface simple sobre o <xref:System.Windows.Forms.BindingSource> componente para que os usuários navegarem entre registros.  
  
### <a name="data-bound-controls"></a>Controles ligados a dados  
 Você pode criar controles associados a dados facilmente usando a janela de fontes de dados, que exibe fontes de dados como bancos de dados, serviços da Web e objetos em seu projeto. Você pode criar controles de associação de dados ao arrastar itens dessa janela para os formulários do seu projeto. Você também pode associar controles existentes a dados ao arrastar objetos da janela Fontes de Dados para eles.  
  
### <a name="settings"></a>Configurações  
 Outro tipo de associação de dados, que você pode gerenciar nos Windows Forms é configurações. A maioria dos aplicativos de cliente inteligente deve manter algumas informações sobre seu estado de tempo de execução, como o último tamanho conhecido de formulários e manter dados de preferência do usuário, como os locais padrão para arquivos salvos. O recurso de configurações do aplicativo lida com esses requisitos, fornecendo uma maneira fácil de armazenar ambos os tipos de configurações no computador cliente. Uma vez definidas usando o Visual Studio ou um editor de código, essas configurações são mantidas como XML e automaticamente lidas para a memória em tempo de execução.  
  
 Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda.  
  
|Para|Consulte|  
|--------|---------|  
|Use o <xref:System.Windows.Forms.BindingSource> componente|[Como: Associar controles dos Windows Forms com o componente BindingSource usando o Designer](../../../framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|Trabalhar com fontes de dados ADO.NET|[Como: Classificar e filtrar dados ADO.NET com o Windows Forms componente BindingSource](../../../framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|Usar a janela fontes de dados|[Passo a passo: Exibindo dados em um Windows Form](/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>Implantando aplicativos em computadores cliente  
 Depois que você tenha escrito o seu aplicativo, você deve enviá-lo para seus usuários para que eles podem instalar e executá-lo em seus próprios computadores cliente. Usando a tecnologia ClickOnce, você pode implantar seus aplicativos no Visual Studio usando apenas alguns cliques e fornecer aos usuários uma URL apontando para seu aplicativo na Web. O ClickOnce gerencia todos os elementos e dependências em seu aplicativo e garante que o aplicativo está instalado corretamente no computador cliente.  
  
 Aplicativos ClickOnce podem ser configurados para executar apenas quando o usuário está conectado à rede, ou para execução online e offline. Quando você especifica que um aplicativo deve oferecer suporte a operação offline, o ClickOnce adiciona um link para seu aplicativo o usuário **iniciar** menu, para que o usuário possa abri-lo sem usar a URL.  
  
 Quando você atualiza o seu aplicativo, publica um novo manifesto de implantação e uma nova cópia do seu aplicativo em seu servidor Web. O ClickOnce detecta que há uma atualização disponível e atualiza a instalação do usuário; nenhuma programação personalizada é necessária para a atualização de assemblies antigos.  
  
 Para obter uma introdução completa ao ClickOnce, consulte [implantação e segurança do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos:  
  
|Para|Consulte|  
|--------|---------|  
|Implantar um aplicativo com ClickOnce|[Como: Publicar um aplicativo ClickOnce usando o assistente de publicação](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Passo a passo: Como implantar manualmente aplicativos ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Atualizar uma implantação do ClickOnce|[Como: Gerenciar atualizações para um aplicativo ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|Gerenciar a segurança com o ClickOnce|[Como: Habilitar configurações de segurança do ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>Outros controles e recursos  
 Existem muitos outros recursos dos Windows Forms que tornam as tarefas comuns de implementação mais fáceis e rápidas, como o suporte à criação de caixas de diálogo, impressão, adição da Ajuda e de documentação e localização do seu aplicativo para diversos idiomas. Além disso, Windows Forms se baseia no sistema de segurança robusto do .NET Framework, permitindo que você ofereça aplicativos mais protegidos aos seus clientes.  
  
 Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos:  
  
|Para|Consulte|  
|--------|---------|  
|Imprimir o conteúdo de um formulário|[Como: Imprimir elementos gráficos nos Windows Forms](../../../framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Como: Imprimir um arquivo de texto de várias páginas nos Windows Forms](../../../framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|   
|Saiba mais sobre a segurança dos Windows Forms|[Visão geral da segurança dos Windows Forms](../../../framework/winforms/security-in-windows-forms-overview.md)|  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [Visão geral dos Windows Forms](../../../framework/winforms/windows-forms-overview.md)
- [Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
