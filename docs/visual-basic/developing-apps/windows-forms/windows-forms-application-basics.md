---
title: "Noções básicas de Aplicativo do Windows Forms (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7872d3c7b19ec9cd7059cccf41e5fab50d85123b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="windows-forms-application-basics-visual-basic"></a>Noções básicas de Aplicativo do Windows Forms (Visual Basic)
Uma parte importante da [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] é a capacidade de criar aplicativos do Windows Forms executados localmente nos computadores dos usuários. Você pode usar o Visual Studio para criar o aplicativo e interface do usuário usando Windows Forms. Um aplicativo Windows Forms baseia-se nas classes do <xref:System.Windows.Forms> namespace.  
  
## <a name="designing-windows-forms-applications"></a>Aplicativos de formulários do Windows de criação  
 Você pode criar formulários do Windows e aplicativos de serviço do Windows com [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]. Para mais informações, consulte os seguintes tópicos:  
  
-   [Guia de Introdução ao Windows Forms](../../../framework/winforms/getting-started-with-windows-forms.md). Fornece informações sobre como criar e programar em Windows Forms.  
   
-   [Controles dos Windows Forms](../../../framework/winforms/controls/index.md). Coleção de tópicos detalhando o uso de controles de formulários do Windows.  
  
-   [Aplicativos de serviço do Windows](../../../framework/windows-services/index.md). Lista os tópicos que explicam como criar serviços do Windows.  
  
## <a name="building-rich-interactive-user-interfaces"></a>Compilando interfaces do usuário sofisticadas e interativas  
 Windows Forms é o componente de cliente inteligente o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], um conjunto de bibliotecas que permitem tarefas comuns de aplicativos como leitura e gravação para o sistema de arquivos. Usando um ambiente de desenvolvimento como [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], você pode criar aplicativos do Windows Forms que exibem informações, solicitam entrada de usuários e se comunicar com computadores remotos em uma rede.  
  
 No Windows Forms, um formulário é uma superfície visual na qual você exibe informações para o usuário. Você normalmente cria aplicativos do Windows Forms colocando controles em formulários e desenvolvendo respostas para ações do usuário, como cliques do mouse ou pressionamentos de teclas. Um *controle* é um elemento discreto de interface do usuário que exibe dados ou aceita a entrada de dados.  
  
### <a name="events"></a>Eventos  
 Quando um usuário faz algo em seu formulário ou um de seus controles, ele gera um evento. O seu aplicativo reage a esses eventos usando código e os processa quando eles acontecem. Para obter mais informações, consulte [Criando manipuladores de eventos nos Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
### <a name="controls"></a>Controles  
 Windows Forms contém uma variedade de controles que você pode colocar em formulários: controles que exibem caixas de texto, botões, caixas suspensas, botões de opção e mesmo páginas da Web. Para obter uma lista de todos os controles que podem ser usados em um formulário, consulte [Controles que podem ser usados nos Windows Forms](../../../framework/winforms/controls/controls-to-use-on-windows-forms.md). Se um controle existente não atender às suas necessidades, os formulários do Windows também oferece suporte à criação de seus próprios controles personalizados usando o <xref:System.Windows.Forms.UserControl> classe.  
  
 O Windows Forms tem controles avançados de interface do usuário que emulam recursos em aplicativos de alta tecnologia, como o Microsoft Office. Usando o <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.MenuStrip> controle, você pode criar barras de ferramentas e menus que contêm texto e imagens, exibem submenus e hospedam outros controles, como caixas de texto e caixas de combinação.  
  
 Com o [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] designer de formulários arrastar e soltar, você pode criar facilmente aplicativos do Windows Forms: apenas selecione os controles com o cursor e colocá-los onde você deseja no formulário. O designer fornece ferramentas, como linhas de grade e "linhas de ajuste" para facilitar o alinhamento de controles. E se você usar [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] ou compilar na linha de comando, você pode usar o <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> e <xref:System.Windows.Forms.SplitContainer> controles para criar avançados layouts de formulários com mínimo de tempo e esforço.  
  
### <a name="custom-ui-elements"></a>Elementos de interface do usuário personalizada  
 Finalmente, se for necessário criar seus próprios elementos personalizados de interface do usuário, o <xref:System.Drawing> namespace contém todas as classes necessárias para processar linhas, círculos e outras formas diretamente em um formulário.  
  
 Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda.  
  
|Para|Consulte|  
|--------|---------|  
|Criar um novo aplicativo Windows Forms com[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]|[Passo a passo: Criando um formulário do Windows simples](http://msdn.microsoft.com/library/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|Usar controles em formulários|[Como Adicionar Controles ao Windows Forms](../../../framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|   
|Criar gráficos com<xref:System.Drawing>|[Introdução à Programação de Elementos Gráficos](../../../framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|Criar controles personalizados|[Como herdar da classe UserControl](../../../framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
## <a name="displaying-and-manipulating-data"></a>Exibindo e manipulando dados  
 Muitos aplicativos precisam exibir dados obtidos de um banco de dados, de um arquivo XML, de um serviço Web XML ou de outra fonte de dados. Windows Forms fornece um controle flexível, chamado de <xref:System.Windows.Forms.DataGridView> controle para o processamento desses dados tabulares em um formato tradicional de linha e coluna, para que cada parte dos dados ocupe sua própria célula. Usando <xref:System.Windows.Forms.DataGridView> pode personalizar a aparência de células individuais, bloquear linhas e colunas em vigor arbitrárias e exibir controles complexos dentro de células, entre outros recursos.  
  
 A conexão a fontes de dados pela rede é uma tarefa simples com clientes inteligentes dos Windows Forms. O <xref:System.Windows.Forms.BindingSource> componente novo no Windows Forms em [!INCLUDE[vsprvslong](~/includes/vsprvslong-md.md)] e [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)], representa uma conexão a uma fonte de dados e expõe métodos para associar dados a controles, navegar para os registros anteriores e posteriores, edição de registros e salvando alterações de volta para a fonte original. O <xref:System.Windows.Forms.BindingNavigator> controle fornece uma interface simple sobre o <xref:System.Windows.Forms.BindingSource> componente para os usuários navegarem entre registros.  
  
### <a name="data-bound-controls"></a>Controles associados a dados  
 Você pode criar controles associados a dados facilmente usando a janela de fontes de dados, que exibe fontes de dados, como bancos de dados, serviços da Web e objetos em seu projeto. Você pode criar controles de associação de dados ao arrastar itens dessa janela para os formulários do seu projeto. Você também pode associar controles existentes a dados ao arrastar objetos da janela Fontes de Dados para eles.  
  
### <a name="settings"></a>Configurações  
 Outro tipo de associação de dados, que você pode gerenciar no Windows Forms é configurações. A maioria dos aplicativos de cliente inteligente devem manter algumas informações sobre seu estado de tempo de execução, como o último tamanho conhecido de formulários e manter dados de preferência do usuário, como locais padrão para arquivos salvos. O recurso de configurações do aplicativo aborda esses requisitos, fornecendo uma maneira fácil de armazenar os dois tipos de configurações no computador cliente. Uma vez definidas usando um [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] ou um editor de código, essas configurações são mantidas como XML e lidas automaticamente de volta na memória em tempo de execução.  
  
 Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda.  
  
|Para|Consulte|  
|--------|---------|  
|Use o <xref:System.Windows.Forms.BindingSource> componente|[Como associar controles dos Windows Forms ao componente BindingSource usando o designer](../../../framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|Trabalhar com [!INCLUDE[vstecado](~/includes/vstecado-md.md)] fontes de dados|[Como classificar e filtrar dados ADO.NET com o componente BindingSource dos Windows Forms](https://msdn.microsoft.com/library/ya3sah92.aspx)|  
|Use a janela fontes de dados|[Passo a passo: exibindo dados em um Windows Form](/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>Implantando aplicativos em computadores cliente  
 Depois de escrever seu aplicativo, você deve enviá-lo para seus usuários para que possam instalar e executá-lo em seus próprios computadores cliente. Usando o [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] tecnologia, você pode implantar seus aplicativos a partir de [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] usando apenas alguns cliques e fornece aos usuários uma URL apontando para seu aplicativo na Web. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]gerencia todos os elementos e dependências em seu aplicativo e garante que o aplicativo está instalado corretamente no computador cliente.  
  
 Os aplicativos [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] podem ser configurados para serem executados somente quando o usuário estiver conectado à rede ou para execução online e offline. Quando você especifica que um aplicativo deve oferecer suporte a operação offline, [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] adiciona um link para seu aplicativo, o usuário **iniciar** menu, para que o usuário pode abri-lo sem usar a URL.  
  
 Quando você atualiza o seu aplicativo, publica um novo manifesto de implantação e uma nova cópia do seu aplicativo em seu servidor Web. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]detecta que há uma atualização disponível e atualiza a instalação do usuário; nenhuma programação personalizada é necessária para atualizar montagens antigas.  
  
 Para obter uma introdução completa [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)], consulte [Implantação e segurança do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos:  
  
|Para|Consulte|  
|--------|---------|  
|Implantar um aplicativo com[!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Passo a passo: implantando um aplicativo ClickOnce manualmente](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Atualizar um [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] implantação|[Como gerenciar atualizações para um aplicativo ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|Gerenciar a segurança com[!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Como habilitar configurações de segurança do ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>Outros controles e recursos  
 Existem muitos outros recursos dos Windows Forms que tornam as tarefas comuns de implementação mais fáceis e rápidas, como o suporte à criação de caixas de diálogo, impressão, adição da Ajuda e de documentação e localização do seu aplicativo para diversos idiomas. Além disso, o Windows Forms depende do sistema de segurança robusto o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], permitindo que você libere aplicativos mais seguros a seus clientes.  
  
 Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos:  
  
|Para|Consulte|  
|--------|---------|  
|Imprimir o conteúdo de um formulário|[Como Imprimir Elementos Gráficos nos Windows Forms](../../../framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Como Imprimir um Arquivo de Texto de Várias Páginas nos Windows Forms](../../../framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|   
|Saiba mais sobre a segurança dos Windows Forms|[Visão geral da segurança dos Windows Forms](../../../framework/winforms/security-in-windows-forms-overview.md)|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 [Visão geral dos Windows Forms](../../../framework/winforms/windows-forms-overview.md)  
 [Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
