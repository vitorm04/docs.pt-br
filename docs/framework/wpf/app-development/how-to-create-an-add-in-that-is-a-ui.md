---
title: 'Como: Criar um suplemento que seja uma interface do usuário'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
ms.openlocfilehash: fa30b7860bd8afdb68b0b54cd8d40f3e1ec86077
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949127"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Como: Criar um suplemento que seja uma interface do usuário
Este exemplo mostra como criar um suplemento que é um Windows Presentation Foundation (WPF) que é hospedado por um aplicativo autônomo do WPF.  
  
 O suplemento é uma IU que é um controle de usuário do WPF. O conteúdo do controle de usuário é um único botão que, quando clicado, exibe uma caixa de mensagem. O aplicativo autônomo do WPF hospeda a interface do usuário do suplemento como o conteúdo da janela principal do aplicativo.  
  
 **Pré-requisitos**  
  
 Este exemplo realça as extensões do WPF para o modelo de suplemento .NET Framework que habilita esse cenário e pressupõe o seguinte:  
  
- Conhecimento do modelo de suplemento .NET Framework, incluindo pipeline, suplemento e desenvolvimento de host. Se você não estiver familiarizado com esses conceitos, consulte [suplementos e extensibilidade](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Para obter um tutorial que demonstre a implementação de um pipeline, um suplemento do e um aplicativo host, consulte [Walkthrough: Criando um aplicativo](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))extensível.  
  
- Conhecimento das extensões do WPF para o modelo de suplemento .NET Framework. Consulte [visão geral dos suplementos do WPF](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Exemplo  
 Criar um suplemento que é uma interface do usuário do WPF requer um código específico para cada segmento de pipeline, o suplemento e o aplicativo host.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementando o segmento de pipeline de contrato

Quando um suplemento é uma interface do usuário, o contrato para o suplemento deve implementar <xref:System.AddIn.Contract.INativeHandleContract>. No exemplo, `IWPFAddInContract` implementa <xref:System.AddIn.Contract.INativeHandleContract>, conforme mostrado no código a seguir.  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementando o segmento de pipeline de exibição de suplemento

Como o suplemento é implementado como uma subclasse do <xref:System.Windows.FrameworkElement> tipo, a exibição do suplemento também deve ser subclasse. <xref:System.Windows.FrameworkElement> O código a seguir mostra a exibição do suplemento do contrato, implementada como a `WPFAddInView` classe.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
Aqui, a exibição do suplemento é derivada de <xref:System.Windows.Controls.UserControl>. Consequentemente, a interface do usuário do suplemento também deve <xref:System.Windows.Controls.UserControl>derivar de.  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementando o segmento de pipeline do adaptador no lado do suplemento

Embora o contrato seja um <xref:System.AddIn.Contract.INativeHandleContract>, o suplemento é um <xref:System.Windows.FrameworkElement> (como especificado pelo segmento de pipeline de exibição do suplemento). Portanto, o <xref:System.Windows.FrameworkElement> deve ser convertido em um <xref:System.AddIn.Contract.INativeHandleContract> antes de cruzar o limite de isolamento. Esse trabalho é executado pelo adaptador do lado do suplemento chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, conforme mostrado no código a seguir.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

No modelo de suplemento em que um suplemento retorna uma interface do usuário (consulte [criar um suplemento que retorna uma interface do usuário](how-to-create-an-add-in-that-returns-a-ui.md)), o adaptador do suplemento converteu o <xref:System.Windows.FrameworkElement> para um <xref:System.AddIn.Contract.INativeHandleContract> chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>também deve ser chamado nesse modelo, embora você precise implementar um método do qual gravar o código para chamá-lo. Você faz isso substituindo <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> e implementando o código que <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> chama se o código que está <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> chamando está esperando <xref:System.AddIn.Contract.INativeHandleContract>um. Nesse caso, o chamador será o adaptador do lado do host, que é abordado em uma seção mais adiante.  
  
> [!NOTE]
> Você também precisa substituir <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> neste modelo para habilitar a Tabulação entre a interface do usuário do aplicativo host e a interface do usuário do suplemento. Para obter mais informações, consulte "limitações do suplemento do WPF" em [visão geral de suplementos do WPF](wpf-add-ins-overview.md).  
  
Como o adaptador do lado do suplemento implementa uma interface derivada de <xref:System.AddIn.Contract.INativeHandleContract>, você também precisa implementar <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>, embora isso seja ignorado quando <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> for substituído.  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementando o segmento de pipeline de exibição de host

Nesse modelo, o aplicativo host normalmente espera que a exibição do host seja uma <xref:System.Windows.FrameworkElement> subclasse. O adaptador do lado do host deve converter <xref:System.AddIn.Contract.INativeHandleContract> o <xref:System.Windows.FrameworkElement> para a após <xref:System.AddIn.Contract.INativeHandleContract> o cruzar o limite de isolamento. Como um método não está sendo chamado pelo aplicativo host para obter o <xref:System.Windows.FrameworkElement>, a exibição do host deve "retornar" <xref:System.Windows.FrameworkElement> ao que o contém. Consequentemente, a exibição do host deve derivar de uma <xref:System.Windows.FrameworkElement> subclasse de que pode conter outras interfaces do <xref:System.Windows.Controls.UserControl>, como. O código a seguir mostra a exibição do host do contrato, implementada `WPFAddInHostView` como a classe.  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementando o segmento de pipeline do adaptador no lado do host

Embora o contrato seja um <xref:System.AddIn.Contract.INativeHandleContract>, o aplicativo host espera um <xref:System.Windows.Controls.UserControl> (conforme especificado pela exibição do host). Consequentemente, <xref:System.AddIn.Contract.INativeHandleContract> o deve ser convertido em <xref:System.Windows.FrameworkElement> um após cruzar o limite de isolamento, antes de ser definido como o conteúdo da exibição do host ( <xref:System.Windows.Controls.UserControl>que deriva de).  
  
O trabalho é executado pelo adaptador no lado do host, conforme mostrado no código a seguir.  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

Como você pode ver, o adaptador do lado do host adquire o <xref:System.AddIn.Contract.INativeHandleContract> chamando o método do <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> adaptador do lado do suplemento (esse é o ponto em que o <xref:System.AddIn.Contract.INativeHandleContract> cruza o limite de isolamento).  
  
O adaptador do lado do host converte o <xref:System.AddIn.Contract.INativeHandleContract> para um <xref:System.Windows.FrameworkElement> chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Por fim, <xref:System.Windows.FrameworkElement> o é definido como o conteúdo da exibição do host.  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implementando os suplementos

Com o adaptador no lado do suplemento e a exibição de suplemento em vigor, o suplemento pode ser implementado derivando da exibição de suplemento, conforme mostrado no código a seguir.  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

Neste exemplo, você pode ver um benefício interessante desse modelo: desenvolvedores de suplementos só precisam implementar o suplemento (já que também é a interface do usuário), em vez de uma classe de suplemento e uma interface do usuário de suplemento.  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a>Implementando o aplicativo host

Com o adaptador do lado do host e o modo de exibição do host criados, o aplicativo host pode usar o modelo de suplemento .NET Framework para abrir o pipeline e adquirir uma exibição do host do suplemento. Essas etapas são mostradas no código a seguir.  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

O aplicativo host usa o código de modelo de suplemento típico .NET Framework para ativar o suplemento, que retorna implicitamente a exibição do host para o aplicativo host. O aplicativo host subsequentemente exibe o modo de exibição do host <xref:System.Windows.Controls.UserControl>(que é <xref:System.Windows.Controls.Grid>um) de um.  
  
 O código para processar interações com a interface do usuário do suplemento é executado no domínio do aplicativo do suplemento. Essas ações incluem o seguinte:  
  
- Manipulando <xref:System.Windows.Controls.Button> o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.  
  
- Mostrando o <xref:System.Windows.MessageBox>.  
  
 Esta atividade é completamente isolada do aplicativo host.  
  
## <a name="see-also"></a>Consulte também

- [Suplementos e extensibilidade](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Visão geral dos suplementos do WPF](wpf-add-ins-overview.md)
