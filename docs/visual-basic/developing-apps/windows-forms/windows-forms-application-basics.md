---
title: "Noções básicas de aplicativo (Visual Basic) do Windows Forms | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8275d3c06ebd89254a07127b4850d32ef0580830
ms.lasthandoff: 03/13/2017

---
# <a name="windows-forms-application-basics-visual-basic"></a>Noções básicas de Aplicativo do Windows Forms (Visual Basic)
Uma parte importante da [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] é a capacidade de criar aplicativos do Windows Forms executados localmente nos computadores dos usuários. Você pode usar o Visual Studio para criar o aplicativo e interface do usuário usando Windows Forms. Um aplicativo Windows Forms se baseia nas classes do <xref:System.Windows.Forms>namespace.</xref:System.Windows.Forms>  
  
## <a name="designing-windows-forms-applications"></a>Aplicativos de formulários do Windows de criação  
 Você pode criar formulários do Windows e aplicativos de serviço do Windows com [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]. Para mais informações, consulte os seguintes tópicos:  
  
-   [Introdução ao Windows Forms](https://msdn.microsoft.com/library/ms229601.aspx). Fornece informações sobre como criar e programar em Windows Forms.  
   
-   [Controles do Windows Forms](https://msdn.microsoft.com/library/ettb6e2a.aspx). Coleção de tópicos detalhando o uso de controles de formulários do Windows.  
  
-   [Aplicativos de serviço do Windows](https://msdn.microsoft.com/library/y817hyb6.aspx). Lista os tópicos que explicam como criar serviços do Windows.  
  
## <a name="building-rich-interactive-user-interfaces"></a>Interfaces do usuário sofisticados e interativos de construção  
 Windows Forms é o componente de cliente inteligente do [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], um conjunto de bibliotecas gerenciadas que habilita tarefas comuns de aplicativos como leitura e gravação para o sistema de arquivos. Usando um ambiente de desenvolvimento como [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], você pode criar aplicativos Windows Forms que exibem informações, solicitam entrada de usuários e se comunicam com computadores remotos em uma rede.  
  
 No Windows Forms, um formulário é uma superfície visual na qual você exibe informações para o usuário. Você normalmente cria aplicativos do Windows Forms colocando controles em formulários e desenvolvendo respostas para ações do usuário, como cliques do mouse ou pressionamentos de teclas. A *controle* é um elemento de interface do usuário do usuário discretos que exibe dados ou aceita entrada de dados.  
  
### <a name="events"></a>Eventos  
 Quando um usuário faz algo em seu formulário ou um de seus controles, ele gera um evento. Seu aplicativo reage a esses eventos usando código e processa os eventos quando eles ocorrem. Para obter mais informações, consulte [Criando manipuladores de eventos em formulários do Windows](https://msdn.microsoft.com/library/dacysss4.aspx).  
  
### <a name="controls"></a>Controles  
 Windows Forms contém uma variedade de controles que você pode colocar em formulários: controles que exibem caixas de texto, botões, caixas suspensas, botões de opção e mesmo páginas da Web. Para obter uma lista de todos os controles que você pode usar em um formulário, consulte [controles para uso em formulários do Windows](https://msdn.microsoft.com/library/3xdhey7w.aspx). Se um controle existente não atender às suas necessidades, Windows Forms também suporta criar seus próprios controles personalizados usando a <xref:System.Windows.Forms.UserControl>classe.</xref:System.Windows.Forms.UserControl>  
  
 Windows Forms possui controles avançados de interface do usuário que emulam recursos em aplicativos avançados como o Microsoft Office. Usando o <xref:System.Windows.Forms.ToolStrip>e <xref:System.Windows.Forms.MenuStrip>controle, você pode criar barras de ferramentas e menus que contêm texto e imagens, exibem submenus e hospedam outros controles como caixas de texto e caixas de combinação.</xref:System.Windows.Forms.MenuStrip> </xref:System.Windows.Forms.ToolStrip>  
  
 Com o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] designer de formulários arrastar-e-soltar, você pode criar facilmente aplicativos do Windows Forms: basta selecionar os controles com o cursor e colocá-los onde você deseja no formulário. O designer fornece ferramentas, como linhas de grade e "linhas de alinhamento" para facilitar o alinhamento dos controles. E se você usar [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] ou compilar na linha de comando, você pode usar o <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel>e <xref:System.Windows.Forms.SplitContainer>controles para criar avançados layouts de formulários com mínimo de tempo e esforço.</xref:System.Windows.Forms.SplitContainer> </xref:System.Windows.Forms.TableLayoutPanel> </xref:System.Windows.Forms.FlowLayoutPanel>  
  
### <a name="custom-ui-elements"></a>Elementos de interface do usuário personalizada  
 Finalmente, se for necessário criar seus próprios elementos personalizados da interface do usuário, o <xref:System.Drawing>namespace contém todas as classes necessárias para processar linhas, círculos e outras formas diretamente em um formulário.</xref:System.Drawing>  
  
 Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda.  
  
|Para|Consulte|  
|--------|---------|  
|Criar um novo aplicativo Windows Forms com[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]|[Passo a passo: Criando um formulário do Windows simples](http://msdn.microsoft.com/en-us/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|Usar controles em formulários|[Como: adicionar controles ao Windows Forms](https://msdn.microsoft.com/library/0h5y8567.aspx)|   
|Criar elementos gráficos com<xref:System.Drawing></xref:System.Drawing>|[Introdução à programação de gráficos](https://msdn.microsoft.com/library/da0f23z7.aspx)|  
|Criar controles personalizados|[Como: herdar da classe UserControl](https://msdn.microsoft.com/library/00ctb4z0.aspx)|  
  
## <a name="displaying-and-manipulating-data"></a>Exibindo e manipulando dados  
 Muitos aplicativos devem exibir dados de um banco de dados, arquivo XML, XML Web Services ou outra fonte de dados. Windows Forms fornece um controle flexível, chamado de <xref:System.Windows.Forms.DataGridView>para o processamento desses dados tabulares em um formato tradicional de linha e coluna, para que cada parte dos dados ocupe sua própria célula.</xref:System.Windows.Forms.DataGridView> Usando <xref:System.Windows.Forms.DataGridView>pode personalizar a aparência de células individuais, bloquear linhas e colunas no lugar arbitrárias e exibir controles complexos dentro de células, entre outros recursos.</xref:System.Windows.Forms.DataGridView>  
  
 Conectar-se a fontes de dados em uma rede é uma tarefa simples com smart clients Windows Forms. O <xref:System.Windows.Forms.BindingSource>componente novo no Windows Forms em [!INCLUDE[vsprvslong](../../../csharp/misc/includes/vsprvslong_md.md)] e [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)], representa uma conexão a uma fonte de dados e expõe métodos para associar dados a controles, navegação para registros anteriores e próximos, editar registros e salvar alterações de volta para a fonte original.</xref:System.Windows.Forms.BindingSource> O <xref:System.Windows.Forms.BindingNavigator>controle fornece uma interface simple sobre o <xref:System.Windows.Forms.BindingSource>componente para os usuários navegarem entre registros.</xref:System.Windows.Forms.BindingSource> </xref:System.Windows.Forms.BindingNavigator>  
  
### <a name="data-bound-controls"></a>Controles ligados a dados  
 Você pode criar controles ligados a dados facilmente usando a janela fontes de dados, que exibe fontes de dados como bancos de dados, Web services e objetos em seu projeto. Você pode criar controles associados a dados arrastando itens dessa janela para formulários em seu projeto. Você também pode associar dados de controles existentes a dados arrastando objetos da janela Data Sources para controles existentes.  
  
### <a name="settings"></a>Configurações  
 Outro tipo de associação de dados, que você pode gerenciar no Windows Forms é configurações. A maioria dos aplicativos de smart-client devem manter algumas informações sobre seu estado de tempo de execução, como o último tamanho conhecido de formulários e manter dados de preferência do usuário, como locais padrão para arquivos salvos. O recurso de configurações do aplicativo aborda esses requisitos, fornecendo uma maneira fácil de armazenar ambos os tipos de configurações no computador cliente. Uma vez definidas usando um [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] ou um editor de código, essas configurações são mantidas como XML e lidas automaticamente de volta na memória em tempo de execução.  
  
 Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos da Ajuda.  
  
|Para|Consulte|  
|--------|---------|  
|Usar o <xref:System.Windows.Forms.BindingSource>componente</xref:System.Windows.Forms.BindingSource>|[Como: associar controles dos Windows Forms com o componente BindingSource usando o Designer](https://msdn.microsoft.com/library/801dxw2t.aspx)|  
|Trabalhar com [!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] fontes de dados|[Como: Classificar e filtrar dados ADO.NET com o componente BindingSource do Windows Forms](https://msdn.microsoft.com/library/ya3sah92.aspx)|  
|Usar a janela fontes de dados|[Passo a passo: exibindo dados em um Windows Form](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>Implantando aplicativos em computadores cliente  
 Depois de escrever seu aplicativo, você deve enviá-la aos seus usuários para que possam instalar e executá-lo em seus próprios computadores cliente. Usando o [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] tecnologia, você pode implantar seus aplicativos de dentro do [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] usando apenas alguns cliques e fornece aos usuários uma URL apontando para seu aplicativo na Web. [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]gerencia todos os elementos e dependências em seu aplicativo e garante que o aplicativo está instalado corretamente no computador cliente.  
  
 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]aplicativos podem ser configurados para executar apenas quando o usuário está conectado à rede, ou para executar ambos online e offline. Quando você especifica que um aplicativo deve oferecer suporte a operação offline, [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] adiciona um link para seu aplicativo do usuário **iniciar** menu, para que o usuário possa abri-lo sem usar a URL.  
  
 Quando você atualiza seu aplicativo, você publica um novo manifesto de implantação e uma nova cópia do seu aplicativo em seu servidor Web. [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]detecta que existe uma atualização disponível e atualiza a instalação do usuário; nenhuma programação personalizada é necessária para atualizar montagens antigas.  
  
 Para obter uma introdução completa [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)], consulte [implantação e segurança do ClickOnce](https://docs.microsoft.com/visualstudio/deployment/clickonce-security-and-deployment). Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos:  
  
|Para|Consulte|  
|--------|---------|  
|Implantar um aplicativo com[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]|[Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](https://docs.microsoft.com/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Passo a passo: implantando um aplicativo ClickOnce manualmente](https://docs.microsoft.com/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Atualizar um [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] implantação|[Como gerenciar atualizações para um aplicativo ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|Gerenciar a segurança com[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]|[Como habilitar configurações de segurança do ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>Outros controles e recursos  
 Há muitos outros recursos no Windows Forms que tornam a implementação de tarefas comuns rápida e fácil, como suporte para criar caixas de diálogo, imprimir, adicionar Ajuda e documentação e localizar seu aplicativo para vários idiomas. Além disso, Windows Forms depende do robusto sistema de segurança de [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], permitindo que você libere aplicativos mais seguros a seus clientes.  
  
 Para obter informações passo a passo sobre como usar esses recursos, consulte os seguintes tópicos:  
  
|Para|Consulte|  
|--------|---------|  
|Imprimir o conteúdo de um formulário|[Como: imprimir elementos gráficos em formulários do Windows](https://msdn.microsoft.com/library/741a0ktc.aspx)<br /><br /> [Como: imprimir um arquivo de texto de várias páginas no Windows Forms](https://msdn.microsoft.com/library/cwbe712d.aspx)|   
|Saiba mais sobre a segurança do Windows Forms|[Security in Windows Forms Overview](https://msdn.microsoft.com/library/90k49ccb.aspx)|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Visão geral do Windows Forms](https://msdn.microsoft.com/library/8bxxy49h.aspx)   
 [Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
