---
title: "Instruções passo a passo: mapeando propriedades usando o controle ElementHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 030183e77a141036416a3bcb8a4c4018df0a7e65
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a>Instruções passo a passo: mapeando propriedades usando o controle ElementHost
Este passo a passo mostra como usar o <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> propriedade mapear [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] propriedades às propriedades correspondentes em hospedado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elemento.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criar o projeto.  
  
-   Definir um novo mapeamento de propriedade.  
  
-   Remover um mapeamento de propriedade padrão.  
  
-   Estender um mapeamento de propriedade padrão.  
  
 Para ver uma listagem de código completa de todas tarefas ilustradas nesta instrução passo a passo, consulte [Mapeando propriedades usando o exemplo de controle ElementHost](http://go.microsoft.com/fwlink/?LinkID=160018).  
  
 Quando você terminar, poderá mapear propriedades [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] para as propriedades [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondentes em um elemento hospedado.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-project"></a>Criando o Projeto  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
1.  Crie um projeto de aplicativo [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] chamado `PropertyMappingWithElementHost`. Para obter mais informações, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  No Gerenciador de Soluções, adicione referências aos assemblies [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a seguir.  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
3.  Copie o seguinte código na parte superior do arquivo de código `Form1`.  
  
     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]  
  
4.  Abra `Form1` no Designer de Formulários do Windows. Clique duas vezes no formulário para adicionar um manipulador de eventos para o <xref:System.Windows.Forms.Form.Load> evento.  
  
5.  Retornar ao Designer de formulários do Windows e adicionar um manipulador de eventos para o formulário <xref:System.Windows.Forms.Control.Resize> eventos. Para obter mais informações, consulte [Como criar manipuladores de eventos usando o Designer](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
6.  Declarar um <xref:System.Windows.Forms.Integration.ElementHost> campo o `Form1` classe.  
  
     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]  
  
## <a name="defining-new-property-mappings"></a>Definindo novos mapeamentos de propriedade  
 O <xref:System.Windows.Forms.Integration.ElementHost> controle fornece vários propriedade mapeamentos padrão. Você adiciona um novo mapeamento de propriedade chamando o <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> método o <xref:System.Windows.Forms.Integration.ElementHost> do controle <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.  
  
#### <a name="to-define-new-property-mappings"></a>Definir novos mapeamentos de propriedade  
  
1.  Copie o código a seguir para a definição da classe `Form1`.  
  
     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]  
  
     O `AddMarginMapping` método adiciona um novo mapeamento para o <xref:System.Windows.Forms.Control.Margin%2A> propriedade.  
  
     O `OnMarginChange` método converte o <xref:System.Windows.Forms.Control.Margin%2A> propriedade para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> propriedade.  
  
2.  Copie o código a seguir para a definição da classe `Form1`.  
  
     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]  
  
     O `AddRegionMapping` método adiciona um novo mapeamento para o <xref:System.Windows.Forms.Control.Region%2A> propriedade.  
  
     O `OnRegionChange` método converte o <xref:System.Windows.Forms.Control.Region%2A> propriedade para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> propriedade.  
  
     O `Form1_Resize` método trata do formulário <xref:System.Windows.Forms.Control.Resize> eventos e dimensiona a região de recorte para encaixar o elemento hospedado.  
  
## <a name="removing-a-default-property-mapping"></a>Removendo um mapeamento de propriedade padrão  
 Remover um mapeamento de propriedade padrão chamando o <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> método sobre o <xref:System.Windows.Forms.Integration.ElementHost> do controle <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.  
  
#### <a name="to-remove-a-default-property-mapping"></a>Remover um mapeamento de propriedade padrão  
  
-   Copie o código a seguir para a definição da classe `Form1`.  
  
     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]  
  
     O `RemoveCursorMapping` método exclui o mapeamento padrão para o <xref:System.Windows.Forms.Control.Cursor%2A> propriedade.  
  
## <a name="extending-a-default-property-mapping"></a>Estendendo um mapeamento de propriedade padrão  
 Você pode usar um mapeamento de propriedade padrão e também estendê-lo com seu próprio mapeamento.  
  
#### <a name="to-extend-a-default-property-mapping"></a>Estender um mapeamento de propriedade padrão  
  
-   Copie o código a seguir para a definição da classe `Form1`.  
  
     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]  
  
     O `ExtendBackColorMapping` método adiciona um tradutor de propriedade personalizada para existente <xref:System.Windows.Forms.Control.BackColor%2A> mapeamento de propriedade.  
  
     O `OnBackColorChange` método define uma imagem específica para o controle hospedado <xref:System.Windows.Controls.Control.Background%2A> propriedade. O método `OnBackColorChange` é chamado depois que o mapeamento de propriedade padrão é aplicado.  
  
## <a name="initializing-your-property-mappings"></a>Inicializando seus mapeamentos de propriedades  
  
#### <a name="to-initialize-your-property-mappings"></a>Inicializar seus mapeamentos de propriedades  
  
1.  Copie o código a seguir para a definição da classe `Form1`.  
  
     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]  
  
     O `Form1_Load` método trata o <xref:System.Windows.Forms.Form.Load> eventos e realiza a seguinte inicialização.  
  
    -   Cria um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> elemento.  
  
    -   Chama os métodos definidos anteriormente no passo a passo para configurar os mapeamentos de propriedade.  
  
    -   Atribui valores iniciais para as propriedades mapeadas.  
  
2.  Pressione F5 para compilar e executar o aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Windows Forms e mapeamento de propriedade do WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Designer do WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Instruções passo a passo: hospedando um controle de composição do WPF nos Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
