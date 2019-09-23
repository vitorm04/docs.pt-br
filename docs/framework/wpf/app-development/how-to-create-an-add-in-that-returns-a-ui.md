---
title: 'Como: Criar um suplemento que retorne uma interface do usuário'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: 1886703e089ed538f68a7221906d815a8ae72076
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182665"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Como: Criar um suplemento que retorne uma interface do usuário
Este exemplo mostra como criar um suplemento que retorna um Windows Presentation Foundation (WPF) para um aplicativo host autônomo do WPF.  
  
 O suplemento retorna uma IU que é um controle de usuário do WPF. O conteúdo do controle de usuário é um único botão que, quando clicado, exibe uma caixa de mensagem. O aplicativo autônomo do WPF hospeda o suplemento e exibe o controle de usuário (retornado pelo suplemento) como o conteúdo da janela principal do aplicativo.  
  
 **Pré-requisitos**  
  
 Este exemplo realça as extensões do WPF para o modelo de suplemento .NET Framework que habilita esse cenário e pressupõe o seguinte:  
  
- Conhecimento do modelo de suplemento .NET Framework, incluindo pipeline, suplemento e desenvolvimento de host. Se você não estiver familiarizado com esses conceitos, consulte [suplementos e extensibilidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Para obter um tutorial que demonstre a implementação de um pipeline, um suplemento do e um aplicativo host, consulte [Walkthrough: Criando um aplicativo](../../add-ins/walkthrough-create-extensible-app.md)extensível.  
  
- Conhecimento das extensões do WPF para o modelo de suplemento .NET Framework, que pode ser encontrado aqui: [Visão geral dos suplementos do WPF](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Exemplo  
 Para criar um suplemento que retorna uma interface do usuário do WPF, é necessário um código específico para cada segmento de pipeline, o suplemento e o aplicativo host.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementando o segmento de pipeline de contrato  
 Um método deve ser definido pelo contrato para retornar uma interface do usuário, e seu valor de retorno deve ser <xref:System.AddIn.Contract.INativeHandleContract>do tipo. Isso é demonstrado pelo `GetAddInUI` método `IWPFAddInContract` do contrato no código a seguir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementando o segmento de pipeline de exibição de suplemento  
 Como [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] o suplemento implementa o que ele fornece como subclasses de <xref:System.Windows.FrameworkElement>, o método na exibição do suplemento que se correlaciona com `IWPFAddInView.GetAddInUI` deve retornar um valor do tipo <xref:System.Windows.FrameworkElement>. O código a seguir mostra a exibição de suplemento do contrato, implementada como uma interface.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementando o segmento de pipeline do adaptador no lado do suplemento  
 O método Contract retorna um <xref:System.AddIn.Contract.INativeHandleContract>, mas o suplemento retorna um <xref:System.Windows.FrameworkElement> (conforme especificado pela exibição do suplemento). Consequentemente, <xref:System.Windows.FrameworkElement> o deve ser convertido em <xref:System.AddIn.Contract.INativeHandleContract> um antes de cruzar o limite de isolamento. Esse trabalho é executado pelo adaptador do lado do suplemento chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, conforme mostrado no código a seguir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementando o segmento de pipeline de exibição de host  
 Como o aplicativo host exibirá um <xref:System.Windows.FrameworkElement>, o método na exibição do host que se correlaciona com `IWPFAddInHostView.GetAddInUI` deve retornar um valor do tipo <xref:System.Windows.FrameworkElement>. O código a seguir mostra a exibição do host do contrato, implementada como uma interface.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementando o segmento de pipeline do adaptador no lado do host  
 O método Contract retorna um <xref:System.AddIn.Contract.INativeHandleContract>, mas o aplicativo host espera um <xref:System.Windows.FrameworkElement> (conforme especificado pela exibição do host). Consequentemente, <xref:System.AddIn.Contract.INativeHandleContract> o deve ser convertido em <xref:System.Windows.FrameworkElement> um depois de cruzar o limite de isolamento. Esse trabalho é executado pelo adaptador do lado do host chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, conforme mostrado no código a seguir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implementando os suplementos  
 Com o adaptador do suplemento e a exibição do suplemento criados, o suplemento`WPFAddIn1.AddIn`() deve implementar o `IWPFAddInView.GetAddInUI` método para retornar um <xref:System.Windows.FrameworkElement> objeto (a <xref:System.Windows.Controls.UserControl> neste exemplo). A implementação do <xref:System.Windows.Controls.UserControl>, `AddInUI`, é mostrada pelo código a seguir.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 A implementação do `IWPFAddInView.GetAddInUI` pelo suplemento simplesmente precisa retornar uma nova instância do `AddInUI`, conforme mostrado pelo código a seguir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>Implementando o aplicativo host  
 Com o adaptador do lado do host e o modo de exibição do host criados, o aplicativo host pode usar o modelo de suplemento .NET Framework para abrir o pipeline, adquirir uma exibição do host do suplemento e chamar `IWPFAddInHostView.GetAddInUI` o método. Essas etapas são mostradas no código a seguir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Consulte também

- [Suplementos e extensibilidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Visão geral dos suplementos do WPF](wpf-add-ins-overview.md)
