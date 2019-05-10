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
ms.openlocfilehash: ccc918a9e8ca5e09cfebf1724519e8e6f9d1d32e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627345"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Como: Criar um suplemento que retorne uma interface do usuário
Este exemplo mostra como criar um suplemento que retorna um Windows Presentation Foundation (WPF) para um host de aplicativo autônomo do WPF.  
  
 O suplemento retorna uma interface do usuário que é um controle de usuário do WPF. O conteúdo do controle de usuário é um único botão que, quando clicado, exibe uma caixa de mensagem. O aplicativo autônomo do WPF hospeda o suplemento e exibe o controle de usuário (retornado pelo suplemento) como o conteúdo da janela principal do aplicativo.  
  
 **Pré-requisitos**  
  
 Este exemplo realça as extensões WPF para o modelo de suplemento do .NET Framework que habilitar esse cenário e pressupõe o seguinte:  
  
- Conhecimento do .NET Framework suplemento do modelo, incluindo o pipeline, suplemento e desenvolvimento de host. Se você estiver familiarizado com esses conceitos, consulte [suplementos e extensibilidade](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Para obter um tutorial que demonstra a implementação de um pipeline, um suplemento e um aplicativo host, consulte [passo a passo: Criando um aplicativo extensível](../../add-ins/walkthrough-create-extensible-app.md).  
  
- Conhecimento das extensões do WPF para o modelo de adicionar do .NET Framework, o que pode ser encontrado aqui: [Visão geral dos suplementos do WPF](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Exemplo  
 Para criar um suplemento que retorna uma UI do WPF requer código específico para cada segmento de pipeline, o suplemento e o aplicativo host.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementando o segmento de pipeline de contrato  
 Um método deve ser definido pelo contrato para retornar uma interface do usuário e seu valor de retorno deve ser do tipo <xref:System.AddIn.Contract.INativeHandleContract>. Isso é demonstrado pelo `GetAddInUI` método da `IWPFAddInContract` de contrato no código a seguir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementando o segmento de pipeline de exibição de suplemento  
 Como o suplemento implementa o [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] fornecidos como subclasses de <xref:System.Windows.FrameworkElement>, o método da exibição do suplemento que se correlaciona com `IWPFAddInView.GetAddInUI` deve retornar um valor do tipo <xref:System.Windows.FrameworkElement>. O código a seguir mostra a exibição de suplemento do contrato, implementada como uma interface.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementando o segmento de pipeline do adaptador no lado do suplemento  
 O método do contrato retorna um <xref:System.AddIn.Contract.INativeHandleContract>, mas o suplemento retorna um <xref:System.Windows.FrameworkElement> (como especificado pela exibição do suplemento). Consequentemente, o <xref:System.Windows.FrameworkElement> deve ser convertido em um <xref:System.AddIn.Contract.INativeHandleContract> antes de cruzar o limite de isolamento. Esse trabalho é executado pelo adaptador do lado do suplemento chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, conforme mostrado no código a seguir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementando o segmento de pipeline de exibição de host  
 Porque o aplicativo host exibe um <xref:System.Windows.FrameworkElement>, o método no modo de host que se correlaciona com `IWPFAddInHostView.GetAddInUI` deve retornar um valor do tipo <xref:System.Windows.FrameworkElement>. O código a seguir mostra a exibição do host do contrato, implementada como uma interface.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementando o segmento de pipeline do adaptador no lado do host  
 O método do contrato retorna um <xref:System.AddIn.Contract.INativeHandleContract>, mas o aplicativo host espera um <xref:System.Windows.FrameworkElement> (como especificado pela exibição host). Consequentemente, o <xref:System.AddIn.Contract.INativeHandleContract> deve ser convertido em um <xref:System.Windows.FrameworkElement> depois de cruzar o limite de isolamento. Esse trabalho é executado pelo adaptador do lado do host chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, conforme mostrado no código a seguir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implementando os suplementos  
 Com o adaptador do lado do suplemento e a exibição suplemento criado, o suplemento (`WPFAddIn1.AddIn`) deve implementar o `IWPFAddInView.GetAddInUI` método retorne um <xref:System.Windows.FrameworkElement> objeto (um <xref:System.Windows.Controls.UserControl> neste exemplo). A implementação de <xref:System.Windows.Controls.UserControl>, `AddInUI`, é mostrado pelo código a seguir.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 A implementação de `IWPFAddInView.GetAddInUI` pelo suplemento simplesmente precisa retornar uma nova instância da `AddInUI`, conforme mostrado pelo código a seguir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>Implementando o aplicativo host  
 Com o adaptador do lado do host e o modo de host criados, o aplicativo host pode usar o modelo de suplemento do .NET Framework para abrir o pipeline, adquirir um modo de exibição de host do suplemento e chamada o `IWPFAddInHostView.GetAddInUI` método. Essas etapas são mostradas no código a seguir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Consulte também

- [Suplementos e extensibilidade](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Visão geral dos suplementos do WPF](wpf-add-ins-overview.md)
