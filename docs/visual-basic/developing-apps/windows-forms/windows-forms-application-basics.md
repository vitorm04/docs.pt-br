---
title: "No&#231;&#245;es b&#225;sicas de aplicativo dos Windows Forms (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Aplicativos do Windows"
  - "Windows Forms, Visual Basic"
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No&#231;&#245;es b&#225;sicas de aplicativo dos Windows Forms (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma parte importante do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] é a capacidade de criar aplicativos do Windows Forms executados localmente nos computadores dos usuários.  Você pode usar o Visual Studio para criar o aplicativo e usuário interface usando Windows Forms.  Um aplicativo WindowsForms é criado no classes do namespace <xref:System.Windows.Forms>.  
  
## Criando aplicativos do Windows Forms  
 Você pode criar aplicativos do Windows Forms e de serviço do Windows com [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)].  Para obter mais informações, consulte os seguintes tópicos:  
  
-   [Guia de introdução ao Windows Forms](../Topic/Getting%20Started%20with%20Windows%20Forms.md).  Fornece informações sobre como criar e o programa Windows Forms.  
  
-   [Windows Forms Walkthroughs](http://msdn.microsoft.com/pt-br/fd44d13d-4733-416f-aefc-32592e59e5d9).  Lista os tópicos que fornecem um desenvolvimento passo a passo dos aplicativos de Windows Forms normalmente criados com base em Windows Forms.  
  
-   [Controles de Windows Forms](../Topic/Windows%20Forms%20Controls.md).  Conjunto de tópicos detalhando o uso de controles de Windows Forms .  
  
-   [Windows Service Applications](../Topic/Developing%20Windows%20Service%20Applications.md).  Lista os tópicos que explicam como criar serviços do Windows.  
  
## Criando interfaces de usuário detalhadas e interativas  
 Windows Forms é o componente de cliente inteligente do [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], um conjunto de bibliotecas que permitem tarefas comuns de aplicativos como leitura e gravação para o sistema de arquivos.  Usando um ambiente de desenvolvimento como [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], você pode criar aplicativos do Windows Forms que exibem informações, solicitam entrada de usuários e se comunicam com computadores remotos em uma rede.  
  
 No Windows Forms, um formulário é uma superfície visual na qual você exibe informações para o usuário.  Você normalmente cria aplicativos do Windows Forms colocando controles em formulários e desenvolvendo respostas para ações do usuário, tais como cliques do mouse ou pressionamentos de teclas.  Um *controle* é um elemento discreto da interface do usuário \(IU\) que exibe dados ou aceita entrada de dados.  
  
### Eventos  
 Quando um usuário faz algo a seu formulário ou a um de seus controles, ele gera um evento.  Seu aplicativo reage a esses eventos usando código e processa os eventos quando eles ocorrem.  Para mais informações, consulte [Criando manipuladores de eventos no Windows Forms](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md).  
  
### Controles  
 Windows Forms contém uma variedade de controles que você pode colocar em formulários: controles que exibem caixas de texto, botões, caixas suspensas, botões de opção e mesmo páginas da Web.  Para obter uma lista de todos os controles que você pode usar em um formulário, consulte [Controles a serem usados nos Windows Forms](../Topic/Controls%20to%20Use%20on%20Windows%20Forms.md).  Se um controle existente não atender suas necessidades, os Formulários do Windows também oferecem suporte à criação de seus próprios controles personalizados através da classe <xref:System.Windows.Forms.UserControl>.  
  
 Windows Forms tem detalhados controles de UI que emulam recursos em aplicativos avançados como o Microsoft Office.  Usando os controles <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.MenuStrip> , você pode criar barras de ferramentas e menus que contêm texto e imagens, exibir submenus e hospedar outros controles como caixas de texto e caixas suspensas.  
  
 Com o recurso de arrastar\-e\-soltar do  designer de formulários [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], você pode facilmente criar aplicativos do Windows Forms: apenas selecione os controles com o seu cursor e coloque\-os onde você deseja no formulário.  O designer fornece ferramentas, como linhas de grade e &quot;linhas de encaixe&quot; para tirar a confusão dos controles de alinhamento.  E se você usar o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] ou compilar na linha de comando, você pode usar os controles <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> e <xref:System.Windows.Forms.SplitContainer> para criar layouts de formulários avançados com tempo e esforços mínimos.  
  
### Personalizado elementos da IU  
 Finalmente, se for necessário criar seus próprios elementos personalizados da IU, o namespace <xref:System.Drawing> contém tudo das classes necessárias para processar linhas, círculos e outras formas diretamente em um formulário.  
  
 Para informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda.  
  
|Para|Consulte|  
|----------|--------------|  
|Criar um novo aplicativo do Windows Forms com [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]|[Walkthrough: Creating a Simple Windows Form](http://msdn.microsoft.com/pt-br/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|Usar controles em formulários|[Como adicionar controles aos Windows Forms](../Topic/How%20to:%20Add%20Controls%20to%20Windows%20Forms.md)|  
|Manipular eventos de um formulário e seus controles|[How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/pt-br/8461e9b8-14e8-406f-936e-3726732b23d2)|  
|Use o controle <xref:System.Windows.Forms.ToolStrip>|[Como criar um ToolStrip básico com itens padrão usando o designer](../Topic/How%20to:%20Create%20a%20Basic%20Windows%20Forms%20ToolStrip%20with%20Standard%20Items%20Using%20the%20Designer.md)|  
|Criar elementos gráficos com <xref:System.Drawing>|[Introdução à programação de elementos gráficos](../Topic/Getting%20Started%20with%20Graphics%20Programming.md)|  
|Criar controles personalizados|[Como herdar da classe UserControl](../Topic/How%20to:%20Inherit%20from%20the%20UserControl%20Class.md)|  
  
## Exibindo e manipulando dados  
 Muitos aplicativos devem exibir dados de um banco de dados, arquivo XML, XML Web Services ou outra fonte de dados.  Windows Forms fornece um controle flexível, denominado controle <xref:System.Windows.Forms.DataGridView>, para processamento desses dados tabulares em um formato tradicional de linha e coluna, para que cada dado ocupe sua própria célula.  Quando você usa <xref:System.Windows.Forms.DataGridView>, você pode personalizar a aparência de células individuais, bloquear linhas e colunas arbitrárias e exibir controles complexos dentro de células, entre outros recursos.  
  
 Conecção a fontes de dados em uma rede é uma tarefa simples com clientes inteligentes do Windows Forms.  O componente <xref:System.Windows.Forms.BindingSource>, novo no Windows Forms no [!INCLUDE[vsprvslong](../../../csharp/misc/includes/vsprvslong_md.md)] e no [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)], representa uma conexão a uma fonte de dados e exibe métodos para associar dados a controles, navegar até registros anteriores e próximos, editar registros e salvas alterações de volta na fonte original.  O controle <xref:System.Windows.Forms.BindingNavigator> fornece uma interface simples sobre o componente <xref:System.Windows.Forms.BindingSource> para os usuários navegarem entre registros.  
  
### Controles associados a dados  
 Você pode criar controles associados a dados facilmente utilizando a janela Data Sources, que exibe fontes de dados como bancos de dados, serviços da Web e objetos em seu projeto.  Você pode criar controles associados a dados arrastando itens dessa janela até formulários do seu projeto.  Você também pode associar dados de controles existentes aos dados arrastando objetos da janela Data Sources até os controles existentes.  
  
### Configurações  
 Outro tipo de associação de dados que você pode gerenciar de Windows Forms é configurações.  A maioria dos aplicativos de cliente inteligente devem manter algumas informações sobre seu estado de tempo de execução, como o último tamanho conhecido de formulários, e manter dados de preferência do usuário, tais como locais padrão para arquivos salvos.  O recurso de configurações do aplicativo endereça esses requisitos, fornecendo uma maneira fácil de armazenar os dois tipos de configurações no computador do cliente.  Uma vez definidas usando um [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] ou um editor de código, essas configurações são mantidas como XML e lidas automaticamente de volta na memória em tempo de execução.  
  
 Para informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda.  
  
|Para|Consulte|  
|----------|--------------|  
|Usar o componente <xref:System.Windows.Forms.BindingSource>|[Como associar controles dos Windows Forms ao componente BindingSource usando o designer](../Topic/How%20to:%20Bind%20Windows%20Forms%20Controls%20with%20the%20BindingSource%20Component%20Using%20the%20Designer.md)|  
|Trabalhar com fontes de dados [!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]|[Como classificar e filtrar dados ADO.NET com o componente BindingSource dos Windows Forms](../Topic/How%20to:%20Sort%20and%20Filter%20ADO.NET%20Data%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)|  
|Usar a janela Data Sources|[Instruções passo a passo: exibindo dados em um Windows Form](../Topic/Walkthrough:%20Displaying%20Data%20on%20a%20Windows%20Form.md)|  
|Usar configurações de aplicativo|[How to: Create Application Settings Using the Designer](http://msdn.microsoft.com/pt-br/53b3af80-1c02-4e35-99c6-787663148945)|  
  
## Implantando aplicativos para computadores de cliente  
 Uma vez que você tenha escrito seu aplicativo, você deve enviá\-lo para os usuários para que eles possam instalá\-lo e executá\-lo em seus próprios computadores de cliente.  Usando o [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] tecnologia, você pode implantar seus aplicativos a partir do [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] por usando apenas alguns cliques e prover usuários com uma URL apontando para seu aplicativo na Web.  [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]gerencia todos os elementos e dependências em seu aplicativo e garante que o aplicativo está instalado corretamente no computador cliente.  
  
 Aplicativos [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] podem ser configurados para executar apenas quando o usuário está conectado à rede, ou para executar ambos online e offline.  Quando você especifica que um aplicativo deve oferecer suporte a operação offline, [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] adiciona um link a seu aplicativo no menu **Start** do usuário, para que o usuário possa abri\-lo sem usar a URL.  
  
 Quando você atualização seu aplicativo, você publicar uma implantaçãonovomanifesto e uma nova cópia do seu aplicativo para o seu servidor Web .   [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]detecta que há uma atualização disponível e atualiza a instalação do usuário; nenhuma programação personalizada é necessária para atualização montagens antigas.  
  
 Para obter uma introdução completa para [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)], consulte [Segurança e implantação do ClickOnce](/visual-studio/deployment/clickonce-security-and-deployment).  Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda:  
  
|Para|Consulte|  
|----------|--------------|  
|Implantar um aplicativo com [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]|[Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)<br /><br /> [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../Topic/Walkthrough:%20Manually%20Deploying%20a%20ClickOnce%20Application.md)|  
|Atualizar uma implantação [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]|[Como gerenciar atualizações para um aplicativo ClickOnce](../Topic/How%20to:%20Manage%20Updates%20for%20a%20ClickOnce%20Application.md)|  
|Gerenciar a segurança com [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]|[Como habilitar configurações de segurança do ClickOnce](../Topic/How%20to:%20Enable%20ClickOnce%20Security%20Settings.md)|  
  
## Outros controles e recursos  
 Há muitos outros recursos no Windows Forms que tornam a implementação de tarefas comuns rápida e fácil, como suporte para criar caixas de diálogo, imprimir, adicionar Ajuda e documentação e localizar seu aplicativo para vários idiomas.  Além disso, Windows Forms depende do robusto sistema de segurança do [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], permitindo que você libere aplicativos mais seguros a seus clientes.  
  
 Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda:  
  
|Para|Consulte|  
|----------|--------------|  
|Imprimir o conteúdo de um formulário|[Como imprimir elementos gráficos no Windows Forms](../Topic/How%20to:%20Print%20Graphics%20in%20Windows%20Forms.md)<br /><br /> [Como imprimir um arquivo de texto de várias páginas no Windows Forms](../Topic/How%20to:%20Print%20a%20Multi-Page%20Text%20File%20in%20Windows%20Forms.md)|  
|Globalizar um aplicativo do Windows Forms|[Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/pt-br/9a96220d-a19b-4de0-9f48-01e5d82679e5)|  
|Aprender mais sobre segurança do Windows Forms|[Visão geral da Segurança do Windows Forms](../Topic/Security%20in%20Windows%20Forms%20Overview.md)|  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Visão geral dos Windows Forms](../Topic/Windows%20Forms%20Overview.md)   
 [Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)