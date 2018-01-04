---
title: "Como criar um suplemento que seja uma interface do usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fea1c718eedb12d49eced9964e4f9045badf07ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Como criar um suplemento que seja uma interface do usuário
Este exemplo mostra como criar um suplemento que é um [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] que é hospedado por um [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo autônomo.  
  
 O suplemento é um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que é um [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] controle de usuário. O conteúdo do controle de usuário é um único botão que, quando clicado, exibe uma caixa de mensagem. O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo autônomo hospeda o suplemento [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] como o conteúdo da janela principal do aplicativo.  
  
 **Pré-requisitos**  
  
 Este exemplo realça o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensões para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] adicionar no modelo de habilitar esse cenário e assume o seguinte:  
  
-   Conhecimento sobre o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] adicionar no modelo, incluindo o pipeline de suplemento e desenvolvimento de host. Se você estiver familiarizado com esses conceitos, consulte [suplementos e extensibilidade](../../../../docs/framework/add-ins/index.md). Para obter um tutorial que demonstra a implementação de um pipeline, um suplemento e um aplicativo host, consulte [passo a passo: Criando um aplicativo extensível](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).  
  
-   Conhecimento do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensões para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] adicionar no modelo, que pode ser encontrado aqui: [visão geral de suplementos WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
## <a name="example"></a>Exemplo  
 Para criar um suplemento que é um [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] requer código específico para cada segmento de pipeline, o suplemento e o aplicativo host.  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implementando o segmento de pipeline de contrato  
 Quando um suplemento é um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], o contrato para o suplemento deve implementar <xref:System.AddIn.Contract.INativeHandleContract>. No exemplo, `IWPFAddInContract` implementa <xref:System.AddIn.Contract.INativeHandleContract>, conforme mostrado no código a seguir.  
  
 [!code-csharp[SimpleAddInIsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]  
  
<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implementando o segmento de pipeline de exibição de suplemento  
 Como o suplemento é implementado como uma subclasse do <xref:System.Windows.FrameworkElement> tipo, o modo de exibição também deve subclasse <xref:System.Windows.FrameworkElement>. O código a seguir mostra a exibição do suplemento do contrato, implementado como o `WPFAddInView` classe.  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
  
 Aqui, o modo de exibição é derivado de <xref:System.Windows.Controls.UserControl>. Consequentemente, o suplemento [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] também deve derivar de <xref:System.Windows.Controls.UserControl>.  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implementando o segmento de pipeline do adaptador no lado do suplemento  
 Enquanto o contrato é um <xref:System.AddIn.Contract.INativeHandleContract>, o suplemento é um <xref:System.Windows.FrameworkElement> (conforme especificado pelo segmento de pipeline de suplemento do modo de exibição). Portanto, o <xref:System.Windows.FrameworkElement> devem ser convertidos para um <xref:System.AddIn.Contract.INativeHandleContract> antes de cruzar o limite de isolamento. O trabalho é executado pelo adaptador do lado do suplemento chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, conforme mostrado no código a seguir.  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
  
 No suplemento do modelo em que um suplemento retorna um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] (consulte [criar um suplemento que retorna uma interface de usuário](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md)), o adaptador de suplemento converte o <xref:System.Windows.FrameworkElement> para um <xref:System.AddIn.Contract.INativeHandleContract> chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>também deve ser chamado nesse modelo, embora você precise implementar um método do qual gravar o código para chamá-lo. Você pode fazer isso por meio da substituição <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> e implementar o código que chama <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> se o código que está chamando <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> está esperando um <xref:System.AddIn.Contract.INativeHandleContract>. Nesse caso, o chamador será o adaptador do lado do host, que é abordado em uma seção mais adiante.  
  
> [!NOTE]
>  Você também precisa substituir <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> nesse modelo para habilitar tabulações entre aplicativo host [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] e suplemento [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Para obter mais informações, consulte "Adicionar limitações de WPF" [visão geral de suplementos WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
 Como o adaptador do lado do suplemento implementa uma interface que deriva de <xref:System.AddIn.Contract.INativeHandleContract>, você também precisa implementar <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>, embora isso seja ignorado quando <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> é substituído.  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implementando o segmento de pipeline de exibição de host  
 Nesse modelo, o aplicativo host tipicamente espera que o modo de host para ser um <xref:System.Windows.FrameworkElement> subclasse. O adaptador do lado do host deve converter o <xref:System.AddIn.Contract.INativeHandleContract> para um <xref:System.Windows.FrameworkElement> depois que o <xref:System.AddIn.Contract.INativeHandleContract> cruzar o limite de isolamento. Como um método não está sendo chamado pelo aplicativo host para obter o <xref:System.Windows.FrameworkElement>, o modo de host deve "retornar" o <xref:System.Windows.FrameworkElement> por que o contém. Consequentemente, o modo de host deve derivar de uma subclasse de <xref:System.Windows.FrameworkElement> que pode conter outros [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], como <xref:System.Windows.Controls.UserControl>. O código a seguir mostra a exibição de host do contrato, implementado como o `WPFAddInHostView` classe.  
  
  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implementando o segmento de pipeline do adaptador no lado do host  
 Enquanto o contrato é um <xref:System.AddIn.Contract.INativeHandleContract>, o aplicativo de host espera um <xref:System.Windows.Controls.UserControl> (como especificado pelo modo de host). Consequentemente, o <xref:System.AddIn.Contract.INativeHandleContract> deve ser convertido em um <xref:System.Windows.FrameworkElement> após cruzar o limite de isolamento, antes de ser definido como conteúdo da exibição de host (que é derivado de <xref:System.Windows.Controls.UserControl>).  
  
 O trabalho é executado pelo adaptador no lado do host, conforme mostrado no código a seguir.  
  
  
  
 Como você pode ver, o adaptador do lado do host adquire o <xref:System.AddIn.Contract.INativeHandleContract> chamando o adaptador do lado do suplemento <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> método (Este é o ponto em que o <xref:System.AddIn.Contract.INativeHandleContract> cruzar o limite de isolamento).  
  
 O adaptador do lado do host converte o <xref:System.AddIn.Contract.INativeHandleContract> para um <xref:System.Windows.FrameworkElement> chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Por fim, o <xref:System.Windows.FrameworkElement> é definido como o conteúdo da exibição do host.  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implementando os suplementos  
 Com o adaptador no lado do suplemento e a exibição de suplemento em vigor, o suplemento pode ser implementado derivando da exibição de suplemento, conforme mostrado no código a seguir.  
  
  
  
  
  
 Neste exemplo, você pode ver um benefício interessante desse modelo: os desenvolvedores suplemento só precisam implementar o suplemento (já que é o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] também), em vez de uma classe do suplemento e um suplemento [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="HostApp"></a>   
## <a name="implementing-the-host-application"></a>Implementando o aplicativo host  
 Com o adaptador do lado do host e o modo de host criados, o aplicativo de host pode usar o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelo de suplemento para abrir a pipeline e adquirir um modo de host do suplemento. Essas etapas são mostradas no código a seguir.  
  
  
  
 O aplicativo host utiliza típico [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] código de modelo de suplemento para ativar o suplemento, que implicitamente retorna o modo de host para o aplicativo host. O aplicativo host subsequentemente exibe o modo de host (que é um <xref:System.Windows.Controls.UserControl>) de um <xref:System.Windows.Controls.Grid>.  
  
 O código para processar interações com o suplemento [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] é executado no domínio de aplicativo do suplemento. Essas ações incluem o seguinte:  
  
-   Tratamento de <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos.  
  
-   Mostrando o <xref:System.Windows.MessageBox>.  
  
 Esta atividade é completamente isolada do aplicativo host.  
  
## <a name="see-also"></a>Consulte também  
 [Suplementos e extensibilidade](../../../../docs/framework/add-ins/index.md)  
 [Visão geral dos suplementos do WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
