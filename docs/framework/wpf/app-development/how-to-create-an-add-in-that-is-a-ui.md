---
title: 'Como: Criar um suplemento que seja uma interface do usuário'
ms.date: 03/30/2017
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
ms.openlocfilehash: 9b7fa33d9af8d364491d1c72813cb62f34378557
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947882"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Como: Criar um suplemento que seja uma interface do usuário
Este exemplo mostra como criar um suplemento que é um Windows Presentation Foundation (WPF) que é hospedado por um aplicativo autônomo do WPF.  
  
 O suplemento é uma interface do usuário que é um controle de usuário do WPF. O conteúdo do controle de usuário é um único botão que, quando clicado, exibe uma caixa de mensagem. O aplicativo autônomo do WPF hospeda o suplemento da interface do usuário como o conteúdo da janela principal do aplicativo.  
  
 **Pré-requisitos**  
  
 Este exemplo realça as extensões WPF para o modelo de suplemento do .NET Framework que habilitar esse cenário e pressupõe o seguinte:  
  
- Conhecimento do .NET Framework suplemento do modelo, incluindo o pipeline, suplemento e desenvolvimento de host. Se você estiver familiarizado com esses conceitos, consulte [suplementos e extensibilidade](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Para obter um tutorial que demonstra a implementação de um pipeline, um suplemento e um aplicativo host, consulte [passo a passo: Criando um aplicativo extensível](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).  
  
- Conhecimento das extensões do WPF para o modelo de suplemento do .NET Framework. Ver [visão geral dos suplementos do WPF](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Exemplo  
 Para criar um suplemento é uma UI do WPF requer código específico para cada segmento de pipeline, o suplemento e o aplicativo host.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementando o segmento de pipeline de contrato  
 Quando um suplemento é uma interface do usuário, o contrato para o suplemento deve implementar <xref:System.AddIn.Contract.INativeHandleContract>. No exemplo, `IWPFAddInContract` implementa <xref:System.AddIn.Contract.INativeHandleContract>, conforme mostrado no código a seguir.  
  
 [!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]  
  
<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementando o segmento de pipeline de exibição de suplemento  
 Como o suplemento é implementado como uma subclasse do <xref:System.Windows.FrameworkElement> tipo, o modo de exibição também deve subclasse <xref:System.Windows.FrameworkElement>. O código a seguir mostra a exibição do suplemento do contrato, implementada como a `WPFAddInView` classe.  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
  
 Aqui, o modo de exibição é derivado de <xref:System.Windows.Controls.UserControl>. Consequentemente, a interface do suplemento também deve derivar de <xref:System.Windows.Controls.UserControl>.  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementando o segmento de pipeline do adaptador no lado do suplemento  
 Enquanto o contrato é um <xref:System.AddIn.Contract.INativeHandleContract>, o suplemento é um <xref:System.Windows.FrameworkElement> (conforme especificado pelo segmento de pipeline de exibição do suplemento). Portanto, o <xref:System.Windows.FrameworkElement> deve ser convertido em um <xref:System.AddIn.Contract.INativeHandleContract> antes de cruzar o limite de isolamento. Esse trabalho é executado pelo adaptador do lado do suplemento chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, conforme mostrado no código a seguir.  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
  
 No suplemento do modelo em que um suplemento retorna uma interface do usuário (consulte [criar um suplemento que retorna uma interface do usuário](how-to-create-an-add-in-that-returns-a-ui.md)), o adaptador de suplemento converte as <xref:System.Windows.FrameworkElement> para um <xref:System.AddIn.Contract.INativeHandleContract> chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> também deve ser chamado nesse modelo, embora você precise implementar um método do qual escrever o código para chamá-lo. Você pode fazer isso por meio da substituição <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> e implementar o código que chama <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> se o código que está chamando <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> está esperando um <xref:System.AddIn.Contract.INativeHandleContract>. Nesse caso, o chamador será o adaptador do lado do host, que é abordado em uma seção mais adiante.  
  
> [!NOTE]
>  Você também precisa substituir <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> nesse modelo para habilitar tabulações entre o aplicativo de host da interface do usuário e da interface do usuário do suplemento. Para obter mais informações, consulte "Adicionar limitações de WPF" em [visão geral de suplementos WPF](wpf-add-ins-overview.md).  
  
 Como o adaptador do lado do suplemento implementa uma interface que deriva de <xref:System.AddIn.Contract.INativeHandleContract>, você também precisa implementar <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>, embora isso seja ignorado quando <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> é substituído.  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementando o segmento de pipeline de exibição de host  
 Nesse modelo, o aplicativo host tipicamente espera que o modo de exibição de host para ser um <xref:System.Windows.FrameworkElement> subclasse. O adaptador do lado do host deve converter o <xref:System.AddIn.Contract.INativeHandleContract> para um <xref:System.Windows.FrameworkElement> depois que o <xref:System.AddIn.Contract.INativeHandleContract> cruza o limite de isolamento. Porque um método não está sendo chamado pelo aplicativo host para obter o <xref:System.Windows.FrameworkElement>, o modo de host deve "retornar" o <xref:System.Windows.FrameworkElement> por que o contém. Consequentemente, a exibição do host deve derivar de uma subclasse de <xref:System.Windows.FrameworkElement> que podem conter outros [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], como <xref:System.Windows.Controls.UserControl>. O código a seguir mostra a exibição de host do contrato, implementada como a `WPFAddInHostView` classe.  

<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementando o segmento de pipeline do adaptador no lado do host  
 Enquanto o contrato é um <xref:System.AddIn.Contract.INativeHandleContract>, o aplicativo host espera um <xref:System.Windows.Controls.UserControl> (como especificado pela exibição host). Consequentemente, o <xref:System.AddIn.Contract.INativeHandleContract> deve ser convertido em um <xref:System.Windows.FrameworkElement> depois de cruzar o limite de isolamento, antes de ser definido como o conteúdo da exibição de host (que é derivada de <xref:System.Windows.Controls.UserControl>).  
  
 O trabalho é executado pelo adaptador no lado do host, conforme mostrado no código a seguir.  

 Como você pode ver, o adaptador do lado do host adquire o <xref:System.AddIn.Contract.INativeHandleContract> chamando o adaptador lado do suplemento <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> método (esse é o ponto em que o <xref:System.AddIn.Contract.INativeHandleContract> cruza o limite de isolamento).  
  
 O adaptador do lado do host, em seguida, converte o <xref:System.AddIn.Contract.INativeHandleContract> para um <xref:System.Windows.FrameworkElement> chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Por fim, o <xref:System.Windows.FrameworkElement> é definido como o conteúdo da exibição de host.  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implementando os suplementos  
 Com o adaptador no lado do suplemento e a exibição de suplemento em vigor, o suplemento pode ser implementado derivando da exibição de suplemento, conforme mostrado no código a seguir.  

 Neste exemplo, você pode ver um benefício interessante desse modelo: os desenvolvedores de suplemento só precisam implementar o suplemento (já que é a interface de usuário), em vez de uma classe do suplemento e uma interface de usuário.  
  
<a name="HostApp"></a>   
## <a name="implementing-the-host-application"></a>Implementando o aplicativo host  
 Com o adaptador do lado do host e o modo de host criados, o aplicativo host pode usar o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelo de suplemento para abrir o pipeline e adquirir um modo de host do suplemento. Essas etapas são mostradas no código a seguir.  

 O aplicativo host usa o código de modelo de suplemento do .NET Framework típico para ativar o suplemento, que implicitamente retorna o modo de exibição de host para o aplicativo host. O aplicativo host posteriormente mostra a exibição de host (que é um <xref:System.Windows.Controls.UserControl>) de um <xref:System.Windows.Controls.Grid>.  
  
 O código para processar interações com o suplemento da interface do usuário é executado no domínio de aplicativo do suplemento. Essas ações incluem o seguinte:  
  
- Manipulando o <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos.  
  
- Mostrando o <xref:System.Windows.MessageBox>.  
  
 Esta atividade é completamente isolada do aplicativo host.  
  
## <a name="see-also"></a>Consulte também

- [Suplementos e extensibilidade](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Visão geral dos suplementos do WPF](wpf-add-ins-overview.md)
