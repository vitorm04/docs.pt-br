---
title: Como criar um suplemento que retorne uma interface do usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: f8323fe35555a56d39c1efed649c2aa3fcf17e43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174583"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Como criar um suplemento que retorne uma interface do usuário
Este exemplo mostra como criar um complemento que retorna um WPF (Windows Presentation Foundation, fundação de apresentação do Windows) para um aplicativo autônomo wpf host.  
  
 O complemento retorna uma UI que é um controle de usuário WPF. O conteúdo do controle de usuário é um único botão que, quando clicado, exibe uma caixa de mensagem. O aplicativo autônomo WPF hospeda o complemento e exibe o controle do usuário (retornado pelo complemento) como o conteúdo da janela principal do aplicativo.  
  
 **Pré-requisitos**  
  
 Este exemplo destaca as extensões do WPF para o modelo de complemento .NET Framework que habilita esse cenário e assume o seguinte:  
  
- Conhecimento do modelo de complemento do .NET Framework, incluindo pipeline, complemento e desenvolvimento de host. Se você não está familiarizado com esses conceitos, consulte [Add-ins e Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Para obter um tutorial que demonstre a implementação de um pipeline, um complemento e um aplicativo host, consulte [Passo a Passo: Criando um Aplicativo Extensível](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).  
  
- Conhecimento das extensões do WPF para o modelo de complemento do Framework .NET, que pode ser encontrado aqui: [Visão geral do WPF Add-Ins](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Exemplo  
 Para criar um complemento que devolva uma UI WPF requer código específico para cada segmento de pipeline, o complemento e o aplicativo host.  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a>Implementando o segmento de pipeline de contrato  
 Um método deve ser definido pelo contrato de devolução de uma <xref:System.AddIn.Contract.INativeHandleContract>UI, e seu valor de retorno deve ser do tipo . Isso é demonstrado `GetAddInUI` pelo `IWPFAddInContract` método do contrato no código a seguir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementando o segmento de pipeline de exibição de suplemento  
 Como o complemento implementa as UIs que <xref:System.Windows.FrameworkElement>fornece como subclasses de , o `IWPFAddInView.GetAddInUI` método na exibição <xref:System.Windows.FrameworkElement>de complemento que se correlaciona deve retornar um valor do tipo . O código a seguir mostra a exibição de suplemento do contrato, implementada como uma interface.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementando o segmento de pipeline do adaptador no lado do suplemento  
 O método de <xref:System.AddIn.Contract.INativeHandleContract>contrato retorna um , <xref:System.Windows.FrameworkElement> mas o complemento retorna a (conforme especificado pela exibição de complemento). Consequentemente, <xref:System.Windows.FrameworkElement> o deve ser <xref:System.AddIn.Contract.INativeHandleContract> convertido em um antes de cruzar o limite de isolamento. Este trabalho é realizado pelo adaptador add-in-side, chamando, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>conforme mostrado no código a seguir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementando o segmento de pipeline de exibição de host  
 Como o aplicativo host <xref:System.Windows.FrameworkElement>exibirá um , o método `IWPFAddInHostView.GetAddInUI` na exibição host <xref:System.Windows.FrameworkElement>que se correlaciona deve retornar um valor do tipo . O código a seguir mostra a exibição do host do contrato, implementada como uma interface.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementando o segmento de pipeline do adaptador no lado do host  
 O método de <xref:System.AddIn.Contract.INativeHandleContract>contrato retorna um <xref:System.Windows.FrameworkElement> , mas o aplicativo host espera um (conforme especificado pela exibição host). Consequentemente, <xref:System.AddIn.Contract.INativeHandleContract> o deve ser <xref:System.Windows.FrameworkElement> convertido para um após cruzar o limite de isolamento. Este trabalho é realizado pelo adaptador <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>do lado do host, chamando, conforme mostrado no código a seguir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a>Implementando os suplementos  
 Com o adaptador add-in e a exibição de complemento`WPFAddIn1.AddIn`criada, `IWPFAddInView.GetAddInUI` o complemento <xref:System.Windows.FrameworkElement> ( <xref:System.Windows.Controls.UserControl> ) deve implementar o método para retornar um objeto (a neste exemplo). A implementação <xref:System.Windows.Controls.UserControl> `AddInUI`do , , é mostrado pelo seguinte código.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 A implementação `IWPFAddInView.GetAddInUI` do complemento simplesmente precisa retornar uma `AddInUI`nova instância de , como mostrado pelo código a seguir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>
## <a name="implementing-the-host-application"></a>Implementando o aplicativo host  
 Com o adaptador do lado do host e a exibição do host criadas, o aplicativo host pode usar o modelo `IWPFAddInHostView.GetAddInUI` de complemento .NET Framework para abrir o pipeline, adquirir uma visão host do complemento e chamar o método. Essas etapas são mostradas no código a seguir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Confira também

- [Suplementos e extensibilidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Visão geral dos suplementos do WPF](wpf-add-ins-overview.md)
