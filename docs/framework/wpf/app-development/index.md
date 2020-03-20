---
title: Desenvolvimento de aplicativo
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: 5ff9f58b72982f79e70b80f60c10828c3b54e5bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185998"
---
# <a name="application-development"></a>Desenvolvimento de aplicativo
<a name="introduction"></a>O Windows Presentation Foundation (WPF) é uma estrutura de apresentação que pode ser usada para desenvolver os seguintes tipos de aplicativos:  
  
- Aplicativos autônomos (aplicativos tradicionais do Windows construídos como conjuntos executáveis que são instalados e executados a partir do computador cliente).  
  
- Aplicativos de navegador XAML (XBAPs) (aplicativos compostos por páginas de navegação que são construídos como conjuntos executáveis e hospedados por navegadores da Web, como o Microsoft Internet Explorer ou o Mozilla Firefox).  
  
- Bibliotecas de controles personalizados (assemblies não executáveis contendo controles reutilizáveis).  
  
- Bibliotecas de classes (assemblies não executáveis que contêm classes reutilizáveis).  
  
> [!NOTE]
> Não é recomendável usar tipos do WPF em um serviço Windows. Se você tentar usar esses recursos em um serviço Windows, será possível que eles não funcionem conforme o esperado.  
  
 Para construir esse conjunto de aplicativos, o WPF implementa uma série de serviços. Este tópico fornece uma visão geral desses serviços e onde encontrar mais informações.  

<a name="Application_Management"></a>
## <a name="application-management"></a>Gerenciamento de Aplicativos  
 Os aplicativos WPF executáveis geralmente requerem um conjunto central de funcionalidadeque inclui o seguinte:  
  
- Criar e gerenciar a infraestrutura de aplicativo comum (incluindo criar um método de ponto de entrada e um loop de mensagem do Windows para receber mensagens de entrada e do sistema).  
  
- Acompanhar o tempo de vida de um aplicativo e interagir com ele.  
  
- Recuperação e processamento de parâmetros de linha de comando.  
  
- Compartilhar recursos [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] e propriedades no escopo do aplicativo.  
  
- Detectar e processar exceções sem tratamento.  
  
- Retornar códigos de saída.  
  
- Gerenciamento de janelas de aplicativos autônomos.  
  
- Rastreamento de navegação em aplicativos de navegador XAML (XBAPs) e aplicativos autônomos com janelas de navegação e quadros.  
  
 Esses recursos são implementados pela classe <xref:System.Windows.Application>, que você adiciona a seus aplicativos usando uma *definição de aplicativo*.  
  
 Para obter mais informações, consulte [Visão geral do gerenciamento de aplicativos](application-management-overview.md).  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>
## <a name="wpf-application-resource-content-and-data-files"></a>Arquivos de recurso, conteúdo e dados do aplicativo WPF  
 O WPF estende o suporte principal no Microsoft .NET Framework para recursos incorporados com suporte para três tipos de arquivos de dados não executáveis: recursos, conteúdo e dados. Para mais informações, consulte [Arquivos de recurso, conteúdo e dados do aplicativo WPF](wpf-application-resource-content-and-data-files.md).  
  
 Um componente-chave do suporte para arquivos de dados não executáveis wpf é a capacidade de identificá-los e carregá-los usando um URI exclusivo. Para obter mais informações, consulte [URIs "pack://" no WPF](pack-uris-in-wpf.md).  
  
<a name="Windows_and_Dialog_Boxes"></a>
## <a name="windows-and-dialog-boxes"></a>Janelas e caixas de diálogo  
 Os usuários interagem com aplicativos autônomos do WPF através do windows. A finalidade de uma janela é hospedar conteúdo do aplicativo e expor a funcionalidade do aplicativo que normalmente permite aos usuários interagir com o conteúdo. No WPF, as janelas <xref:System.Windows.Window> são encapsuladas pela classe, que suporta:  
  
- Cria e exibir janelas.  
  
- Estabelecer relações de janela de proprietário/propriedade.  
  
- Configurar a aparência da janela (por exemplo, tamanho, localização, ícones, texto da barra de título, borda).  
  
- Acompanhar o tempo de vida de uma janela e interagir com ele.  
  
 Para obter mais informações, consulte [Visão geral do WPF do Windows](wpf-windows-overview.md).  
  
 <xref:System.Windows.Window> é compatível com a criação de um tipo especial de janela conhecido como caixa de diálogo. Tipos modais e sem janela restrita de caixas de diálogo podem ser criados.  
  
 Para conveniência e os benefícios da reutilização e uma experiência de usuário consistente entre aplicativos, <xref:Microsoft.Win32.OpenFileDialog> <xref:Microsoft.Win32.SaveFileDialog>o <xref:System.Windows.Controls.PrintDialog>WPF expõe três das caixas de diálogo comuns do Windows: , e .  
  
 Uma caixa de mensagem é um tipo especial de caixa de diálogo para mostrar informações textuais importantes para os usuários e para fazer perguntas simples como Sim/Não/OK/Cancelar. Use a classe <xref:System.Windows.MessageBox> para criar e exibir caixas de mensagem.  
  
 Para obter mais informações, consulte [Visão geral das caixas de diálogo](dialog-boxes-overview.md).  
  
<a name="Navigation"></a>
## <a name="navigation"></a>Navegação  
 O WPF suporta navegação no<xref:System.Windows.Controls.Page>estilo Web usando<xref:System.Windows.Documents.Hyperlink>páginas () e hiperlinks ( ). A navegação pode ser implementada de uma variedade de formas, que incluem o seguinte:  
  
- Páginas autônomas que são hospedadas em um navegador da Web.  
  
- Páginas compiladas em um XBAP hospedado em um navegador da Web.  
  
- Páginas compiladas em um aplicativo autônomo e hospedadas por uma janela de navegação (<xref:System.Windows.Navigation.NavigationWindow>).  
  
- Páginas hospedadas por um<xref:System.Windows.Controls.Frame>quadro ( ), que podem ser hospedadas em uma página autônoma ou uma página compilada em um XBAP ou um aplicativo autônomo.  
  
 Para facilitar a navegação, o WPF implementa o seguinte:  
  
- <xref:System.Windows.Navigation.NavigationService>, o mecanismo de navegação compartilhada para solicitações de navegação de processamento que é usado por <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>e XBAPs para suportar a navegação intra-aplicativo.  
  
- Métodos de navegação para iniciar a navegação.  
  
- Eventos de navegação para monitorar e interagir com o tempo de vida de navegação.  
  
- Lembrar-se da navegação progressiva e regressiva usando um diário, que também pode ser inspecionado e manipulado.  
  
 Para obter informações, consulte [Visão geral de navegação](navigation-overview.md).  
  
 O WPF também suporta um tipo especial de navegação conhecido como navegação estruturada. A navegação estruturada pode ser usada para chamar uma ou mais páginas que retornam dados de forma estruturada e previsível, consistente com a chamada de funções. Essa funcionalidade depende da classe <xref:System.Windows.Navigation.PageFunction%601>, que é descrita posteriormente em [Visão geral da navegação estruturada](structured-navigation-overview.md). O <xref:System.Windows.Navigation.PageFunction%601> também serve para simplificar a criação de topologias complexas de navegação, que são descritas em [Visão geral de topologias de navegação](navigation-topologies-overview.md).  
  
<a name="Hosting"></a>
## <a name="hosting"></a>Hosting  
 XBAPs podem ser hospedados no Microsoft Internet Explorer ou Firefox. Cada modelo de hospedagem tem seu próprio conjunto de considerações e restrições que são abordados em [Hospedagem](hosting-wpf-applications.md).  
  
<a name="Build_and_Deploy"></a>
## <a name="build-and-deploy"></a>Compilar e implantar  
 Embora aplicativos WPF simples possam ser construídos a partir de um prompt de comando usando compiladores de linha de comando, o WPF se integra ao Visual Studio para fornecer suporte adicional que simplificou o processo de desenvolvimento e construção. Para obter mais informações, consulte [Compilando um aplicativo WPF](building-a-wpf-application-wpf.md).  
  
 Dependendo do tipo de aplicativo que você compilar, há uma ou mais opções de implantação para escolher. Para obter mais informações, consulte [Implantando um aplicativo WPF](deploying-a-wpf-application-wpf.md).  
  
<a name="related_topics"></a>
## <a name="related-topics"></a>Tópicos Relacionados  
  
|Title|Descrição|  
|-----------|-----------------|  
|[Visão geral de gerenciamento do aplicativo](application-management-overview.md)|Fornece uma visão geral da classe <xref:System.Windows.Application>, incluindo o gerenciamento do tempo de vida do aplicativo, janelas, recursos de aplicativos e navegação.|  
|[Janelas no WPF](windows-in-wpf-applications.md)|Fornece detalhes do gerenciamento de janelas em seu aplicativo, incluindo como usar a classe <xref:System.Windows.Window> e caixas de diálogo.|  
|[Visão geral da navegação](navigation-overview.md)|Fornece uma visão geral do gerenciamento de navegação entre páginas do seu aplicativo.|  
|[Hospedagem](hosting-wpf-applications.md)|Fornece uma visão geral dos aplicativos do navegador XAML (XBAPs).|  
|[Construir e implantar](building-and-deploying-wpf-applications.md)|Descreve como compilar e implantar seu aplicativo WPF.|  
|[Introdução ao WPF no Visual Studio](../getting-started/introduction-to-wpf-in-vs.md)|Descreve os principais recursos do WPF.|  
|[Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|Um passo a passo que mostra como criar um aplicativo WPF usando a navegação de página, layout, controles, imagens, estilos e associação.|
