---
title: Desenvolvimento do aplicativo
ms.custom: ''
ms.date: 01/26/2018
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 22d0b54fa6e75e47fa62b6323c64ec86ddd07008
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="application-development"></a>Desenvolvimento do aplicativo
<a name="introduction"></a> Windows Presentation Foundation (WPF) é uma estrutura de apresentação que pode ser usada para desenvolver os seguintes tipos de aplicativos:  
  
-   Aplicativos autônomos (aplicativos [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] de estilo tradicional criados como assemblies executáveis que são instalados e executados do computador cliente).  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] (aplicativos compostos de páginas de navegação que são criados como assemblies executáveis e hospedados por navegadores da Web, como o [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] ou o Mozilla Firefox).  
  
-   Bibliotecas de controles personalizados (assemblies não executáveis contendo controles reutilizáveis).  
  
-   Bibliotecas de classes (assemblies não executáveis que contêm classes reutilizáveis).  
  
> [!NOTE]
>  Não é recomendável usar tipos do WPF em um serviço Windows. Se você tentar usar esses recursos em um serviço Windows, será possível que eles não funcionem conforme o esperado.  
  
 Para compilar esse conjunto de aplicativos, o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implementa uma gama de serviços. Este tópico fornece uma visão geral desses serviços e onde encontrar mais informações.  
  

  
<a name="Application_Management"></a>   
## <a name="application-management"></a>Gerenciamento de aplicativos  
 Aplicativos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] executáveis frequentemente requerem um conjunto principal de funcionalidades que inclui o seguinte:  
  
-   Criar e gerenciar a infraestrutura de aplicativo comum (incluindo criar um método de ponto de entrada e um loop de mensagem do Windows para receber mensagens de entrada e do sistema).  
  
-   Acompanhar o tempo de vida de um aplicativo e interagir com ele.  
  
-   Recuperar e processar parâmetros de linha de comando.  
  
-   Compartilhar recursos [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] e propriedades no escopo do aplicativo.  
  
-   Detectar e processar exceções sem tratamento.  
  
-   Retornar códigos de saída.  
  
-   Gerenciar janelas de aplicativos autônomas.  
  
-   Acompanhar a navegação em [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] e aplicativos autônomos com quadros e janelas de navegação.  
  
 Esses recursos são implementados pela classe <xref:System.Windows.Application>, que você adiciona a seus aplicativos usando uma *definição de aplicativo*.  
  
 Para obter mais informações, consulte [Visão geral do gerenciamento de aplicativos](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## <a name="wpf-application-resource-content-and-data-files"></a>Arquivos de recurso, conteúdo e dados do aplicativo WPF  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] estende o suporte central no Microsoft .NET Framework para recursos inseridos com suporte para três tipos de arquivos de dados não executáveis: recurso, conteúdo e dados. Para mais informações, consulte [Arquivos de recurso, conteúdo e dados do aplicativo WPF](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).  
  
 Um componente chave do suporte para arquivos de dados não executáveis do WPF é a capacidade de identificar e carregá-los usando um único [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Para obter mais informações, consulte [URIs "pack://" no WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## <a name="windows-and-dialog-boxes"></a>Janelas e caixas de diálogo  
 Os usuários interagem com aplicativos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] autônomos por meio de janelas. A finalidade de uma janela é hospedar conteúdo do aplicativo e expor a funcionalidade do aplicativo que normalmente permite aos usuários interagir com o conteúdo. No [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], as janelas são encapsuladas pela classe <xref:System.Windows.Window>, que permite:  
  
-   Criar e exibir janelas.  
  
-   Estabelecer relações de janela de proprietário/propriedade.  
  
-   Configurar a aparência da janela (por exemplo, tamanho, localização, ícones, texto da barra de título, borda).  
  
-   Acompanhar o tempo de vida de uma janela e interagir com ele.  
  
 Para obter mais informações, consulte [Visão geral do WPF do Windows](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).  
  
 <xref:System.Windows.Window> é compatível com a criação de um tipo especial de janela conhecido como caixa de diálogo. Tipos modais e sem janela restrita de caixas de diálogo podem ser criados.  
  
 Para sua conveniência, os benefícios de reutilização e uma experiência de usuário consistente em todos os aplicativos, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] expõe três caixas de diálogo comuns do Windows: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, e <xref:System.Windows.Controls.PrintDialog>.  
  
 Uma caixa de mensagem é um tipo especial de caixa de diálogo para mostrar informações textuais importantes para os usuários e para fazer perguntas simples como Sim/Não/OK/Cancelar. Use a classe <xref:System.Windows.MessageBox> para criar e exibir caixas de mensagem.  
  
 Para obter mais informações, consulte [Visão geral das caixas de diálogo](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Navegação  
 O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] oferece suporte à navegação no estilo da Web por meio de páginas (<xref:System.Windows.Controls.Page>) e hiperlinks (<xref:System.Windows.Documents.Hyperlink>). A navegação pode ser implementada de uma variedade de formas, que incluem o seguinte:  
  
-   Páginas autônomas que são hospedadas em um navegador da Web.  
  
-   Páginas compiladas em um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] que é hospedado em um navegador da Web.  
  
-   Páginas compiladas em um aplicativo autônomo e hospedadas por uma janela de navegação (<xref:System.Windows.Navigation.NavigationWindow>).  
  
-   Páginas hospedadas por um quadro (<xref:System.Windows.Controls.Frame>), que pode ser hospedado em uma página autônoma, ou uma página compilada em um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ou um aplicativo autônomo.  
  
 Para facilitar a navegação, o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implementa o seguinte:  
  
-   <xref:System.Windows.Navigation.NavigationService>, o mecanismo de navegação compartilhada para processar solicitações de navegação que é usado por <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow> e [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] para oferecer suporte à navegação intra-aplicativo.  
  
-   Métodos de navegação para iniciar a navegação.  
  
-   Eventos de navegação para monitorar e interagir com o tempo de vida de navegação.  
  
-   Lembrar-se da navegação progressiva e regressiva usando um diário, que também pode ser inspecionado e manipulado.  
  
 Para obter informações, consulte [Visão geral de navegação](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
 O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] também dá suporte a um tipo especial de navegação conhecido como navegação estruturada. A navegação estruturada pode ser usada para chamar uma ou mais páginas que retornam dados de forma estruturada e previsível, consistente com a chamada de funções. Essa funcionalidade depende da classe <xref:System.Windows.Navigation.PageFunction%601>, que é descrita posteriormente em [Visão geral da navegação estruturada](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md). O <xref:System.Windows.Navigation.PageFunction%601> também serve para simplificar a criação de topologias complexas de navegação, que são descritas em [Visão geral de topologias de navegação](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md).  
  
<a name="Hosting"></a>   
## <a name="hosting"></a>Hospedagem  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] pode ser hospedado em [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] ou o no Firefox. Cada modelo de hospedagem tem seu próprio conjunto de considerações e restrições que são abordados em [Hospedagem](../../../../docs/framework/wpf/app-development/hosting-wpf-applications.md).  
  
<a name="Build_and_Deploy"></a>   
## <a name="build-and-deploy"></a>Compilar e implantar  
 Embora aplicativos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] simples possam ser criados por meio de um prompt de comando usando compiladores de linha de comando, o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] se integra ao [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] para dar suporte adicional que simplifica o processo de build e desenvolvimento. Para obter mais informações, consulte [Compilando um aplicativo WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
 Dependendo do tipo de aplicativo que você compilar, há uma ou mais opções de implantação para escolher. Para obter mais informações, consulte [Implantando um aplicativo WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md).  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Visão geral do gerenciamento de aplicativos](../../../../docs/framework/wpf/app-development/application-management-overview.md)|Fornece uma visão geral da classe <xref:System.Windows.Application>, incluindo o gerenciamento do tempo de vida do aplicativo, janelas, recursos de aplicativos e navegação.|  
|[Janelas no WPF](../../../../docs/framework/wpf/app-development/windows-in-wpf-applications.md)|Fornece detalhes do gerenciamento de janelas em seu aplicativo, incluindo como usar a classe <xref:System.Windows.Window> e caixas de diálogo.|  
|[Visão geral de navegação](../../../../docs/framework/wpf/app-development/navigation-overview.md)|Fornece uma visão geral do gerenciamento de navegação entre páginas do seu aplicativo.|  
|[Hospedagem](../../../../docs/framework/wpf/app-development/hosting-wpf-applications.md)|Apresenta uma visão geral de [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].|  
|[Compilar e implantar](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md)|Descreve como compilar e implantar seu aplicativo WPF.|  
|[Introdução ao WPF no Visual Studio](../../../../docs/framework/wpf/getting-started/introduction-to-wpf-in-vs.md)|Descreve os principais recursos do WPF.|  
|[Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)|Um passo a passo que mostra como criar um aplicativo WPF usando a navegação de página, layout, controles, imagens, estilos e associação.|
