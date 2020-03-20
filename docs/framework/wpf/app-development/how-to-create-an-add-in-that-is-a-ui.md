---
title: Como criar um suplemento que seja uma interface do usuário
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
ms.openlocfilehash: 339231031b9e57b9f00a2aeb6fbbde8ad66c1ad9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141023"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Como criar um suplemento que seja uma interface do usuário
Este exemplo mostra como criar um complemento que é um WPF (Windows Presentation Foundation, fundação de apresentação do Windows) que é hospedado por um aplicativo autônomo WPF.  
  
 O complemento é uma ui que é um controle de usuário WPF. O conteúdo do controle de usuário é um único botão que, quando clicado, exibe uma caixa de mensagem. O aplicativo autônomo WPF hospeda a interface do crédito como o conteúdo da janela principal do aplicativo.  
  
 **Pré-requisitos**  
  
 Este exemplo destaca as extensões do WPF para o modelo de complemento .NET Framework que habilita esse cenário e assume o seguinte:  
  
- Conhecimento do modelo de complemento do .NET Framework, incluindo pipeline, complemento e desenvolvimento de host. Se você não está familiarizado com esses conceitos, consulte [Add-ins e Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Para obter um tutorial que demonstre a implementação de um pipeline, um complemento e um aplicativo host, consulte [Passo a Passo: Criando um Aplicativo Extensível](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).  
  
- Conhecimento das extensões do WPF para o modelo de complemento .NET Framework. Consulte [a visão geral do WPF Add-Ins](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Exemplo  
 Para criar um complemento que seja um WPF UI requer código específico para cada segmento de pipeline, o complemento e o aplicativo host.  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a>Implementando o segmento de pipeline de contrato

Quando um complemento é uma ui, o contrato <xref:System.AddIn.Contract.INativeHandleContract>para o complemento deve ser implementado . No exemplo, `IWPFAddInContract` implementa, <xref:System.AddIn.Contract.INativeHandleContract>como mostrado no código a seguir.  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementando o segmento de pipeline de exibição de suplemento

Como o complemento é implementado como <xref:System.Windows.FrameworkElement> uma subclasse do tipo, a <xref:System.Windows.FrameworkElement>exibição de complemento também deve subclasse . O código a seguir mostra o complemento do `WPFAddInView` contrato, implementado como classe.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
Aqui, a visão de complemento <xref:System.Windows.Controls.UserControl>é derivada de . Consequentemente, a ui add-in <xref:System.Windows.Controls.UserControl>também deve derivar de .  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementando o segmento de pipeline do adaptador no lado do suplemento

Embora o contrato <xref:System.AddIn.Contract.INativeHandleContract>seja um , <xref:System.Windows.FrameworkElement> o complemento é um (conforme especificado pelo segmento de pipeline de exibição adicional). Portanto, o <xref:System.Windows.FrameworkElement> deve ser convertido <xref:System.AddIn.Contract.INativeHandleContract> em um antes de cruzar o limite de isolamento. Este trabalho é realizado pelo adaptador add-in-side, chamando, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>conforme mostrado no código a seguir.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

No modelo adicional em que um add-in retorna uma UI (ver [Criar um Add-In That Returns a UI),](how-to-create-an-add-in-that-returns-a-ui.md)o adaptador add-in converteu o <xref:System.Windows.FrameworkElement> para um <xref:System.AddIn.Contract.INativeHandleContract> chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>também deve ser chamado neste modelo, embora você precise implementar um método a partir do qual escrever o código para chamá-lo. Você faz isso <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> substituindo e implementando o código que chama <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> se o código que está chamando <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> está esperando um <xref:System.AddIn.Contract.INativeHandleContract>. Nesse caso, o chamador será o adaptador do lado do host, que é abordado em uma seção mais adiante.  
  
> [!NOTE]
> Você também precisa <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> substituir neste modelo para ativar a tabulação entre a interface do e-u ide do aplicativo host e a interface do motorista. Para obter mais informações, consulte "Limitações adicionais do WPF" na [visão geral do WPF Add-Ins](wpf-add-ins-overview.md).  
  
Como o adaptador add-in-side implementa uma <xref:System.AddIn.Contract.INativeHandleContract>interface derivada, <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>você também precisa <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> implementar, embora isso seja ignorado quando é substituído.  
  
<a name="HostViewPipeline"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementando o segmento de pipeline de exibição de host

Neste modelo, o aplicativo host normalmente espera <xref:System.Windows.FrameworkElement> que a exibição host seja uma subclasse. O adaptador do lado <xref:System.AddIn.Contract.INativeHandleContract> do <xref:System.Windows.FrameworkElement> host <xref:System.AddIn.Contract.INativeHandleContract> deve converter o para um após o cruzamento do limite de isolamento. Como um método não está sendo chamado pelo <xref:System.Windows.FrameworkElement>aplicativo host para obter <xref:System.Windows.FrameworkElement> o , a exibição host deve "retornar" o contendo-o. Consequentemente, a exibição host deve <xref:System.Windows.FrameworkElement> derivar de uma subclasse <xref:System.Windows.Controls.UserControl>que pode conter outras UIs, tais como . O código a seguir mostra a visão `WPFAddInHostView` do host do contrato, implementado como classe.  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementando o segmento de pipeline do adaptador no lado do host

Embora o contrato <xref:System.AddIn.Contract.INativeHandleContract>seja um , <xref:System.Windows.Controls.UserControl> o aplicativo host espera um (conforme especificado pela exibição host). Consequentemente, <xref:System.AddIn.Contract.INativeHandleContract> o deve ser <xref:System.Windows.FrameworkElement> convertido para um após cruzar o limite de isolamento, antes <xref:System.Windows.Controls.UserControl>de ser definido como conteúdo da exibição do host (que deriva de ).  
  
O trabalho é executado pelo adaptador no lado do host, conforme mostrado no código a seguir.  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

Como você pode ver, o adaptador <xref:System.AddIn.Contract.INativeHandleContract> do lado do host adquire o <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> chamando de método do <xref:System.AddIn.Contract.INativeHandleContract> adaptador add-in-side (este é o ponto onde o cruzamento cruza o limite de isolamento).  
  
O adaptador do lado do <xref:System.AddIn.Contract.INativeHandleContract> host <xref:System.Windows.FrameworkElement> então <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>converte o para um chamando . Finalmente, <xref:System.Windows.FrameworkElement> o é definido como o conteúdo da exibição do host.  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a>Implementando os suplementos

Com o adaptador no lado do suplemento e a exibição de suplemento em vigor, o suplemento pode ser implementado derivando da exibição de suplemento, conforme mostrado no código a seguir.  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

A partir deste exemplo, você pode ver um benefício interessante deste modelo: desenvolvedores adicionais só precisam implementar o complemento (já que é a ui também), em vez de uma classe adicional e uma ui adicional.  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a>Implementando o aplicativo host

Com o adaptador do lado do host e a exibição do host criadas, o aplicativo host pode usar o modelo de complemento .NET Framework para abrir o pipeline e adquirir uma visão host do complemento. Essas etapas são mostradas no código a seguir.  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

O aplicativo host usa o código de modelo de complemento típico do .NET Framework para ativar o complemento, que retorna implicitamente a exibição host para o aplicativo host. O aplicativo host exibe posteriormente a <xref:System.Windows.Controls.UserControl>exibição <xref:System.Windows.Controls.Grid>do host (que é a) a partir de um .  
  
 O código para processar interações com a interface do usuário é executado no domínio do aplicativo do add-in. Essas ações incluem o seguinte:  
  
- Cuidando do <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.  
  
- Mostrando <xref:System.Windows.MessageBox>o .  
  
 Esta atividade é completamente isolada do aplicativo host.  
  
## <a name="see-also"></a>Confira também

- [Suplementos e extensibilidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Visão geral dos suplementos do WPF](wpf-add-ins-overview.md)
