---
title: 'O modelo de objeto Ink: Windows Forms e COM versus WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling ink [WPF]
- InkCanvas control [WPF]
- ink object model [WPF]
- tablet pen [WPF], events [WPF]
- ink [WPF], enabling
- events [WPF], tablet pen
ms.assetid: 577835be-b145-4226-8570-1d309e9b3901
ms.openlocfilehash: 2c0d155d320bab2f0114280e962c8f2f0b559681
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636413"
---
# <a name="the-ink-object-model-windows-forms-and-com-versus-wpf"></a>O modelo de objeto Ink: Windows Forms e COM versus WPF

Há basicamente três plataformas que dão suporte à tinta digital: a plataforma de Windows Forms do Tablet PC, a plataforma COM do Tablet PC e a plataforma do Windows Presentation Foundation (WPF).  As plataformas Windows Forms e COM compartilham um modelo de objeto semelhante, mas o modelo de objeto para a plataforma WPF é substancialmente diferente.  Este tópico discute as diferenças em um alto nível para que os desenvolvedores que trabalharam com um modelo de objetos possam entender o outro.  
  
## <a name="enabling-ink-in-an-application"></a>Habilitando o Ink em um aplicativo  
 Todas as três plataformas vêm com objetos e controles que permitem que um aplicativo receba entrada de uma caneta eletrônica.  As plataformas Windows Forms e COM são fornecidas com as classes [Microsoft. Ink. InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)), [Microsoft. Ink. InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90)), [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)) e [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) .  [Microsoft. Ink. InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)) e [Microsoft. Ink. InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90)) são controles que você pode adicionar a um aplicativo para coletar tinta.  O [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)) e [o Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) podem ser anexados a uma janela existente para habilitar o Windows e controles personalizados por tinta.  
  
 A plataforma WPF inclui o controle <xref:System.Windows.Controls.InkCanvas>.  Você pode adicionar um <xref:System.Windows.Controls.InkCanvas> ao seu aplicativo e começar a coletar tinta imediatamente. Com o <xref:System.Windows.Controls.InkCanvas>, o usuário pode copiar, selecionar e redimensionar a tinta.  Você pode adicionar outros controles à <xref:System.Windows.Controls.InkCanvas>, e o usuário também pode escrever sobre esses controles.  Você pode criar um controle personalizado habilitado para tinta adicionando um <xref:System.Windows.Controls.InkPresenter> a ele e coletando seus pontos de Stylus.  
  
 A tabela a seguir lista em que você pode saber mais sobre como habilitar a tinta em um aplicativo:  
  
|Para fazer isso...|Na plataforma WPF...|Nas plataformas Windows Forms/COM...|  
|-----------------|--------------------------|------------------------------------------|  
|Adicionar um controle habilitado para tinta a um aplicativo|Consulte [Introdução à tinta](getting-started-with-ink.md).|Consulte [Exemplo de formulário de declarações automáticas](/windows/desktop/tablet/auto-claims-form-sample)|  
|Habilitar tinta em um controle personalizado|Consulte [Criando um controle de entrada de tinta](creating-an-ink-input-control.md).|Consulte [Exemplo da área de transferência de tinta](/windows/desktop/tablet/ink-clipboard-sample).|  
  
## <a name="ink-data"></a>Dados de tinta  
 Nas plataformas Windows Forms e COM, o [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)), [o Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)), [o Microsoft. Ink. InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90))e [o Microsoft. Ink. InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)) expõem um objeto [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) . O objeto [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) contém os dados de um ou mais objetos [Microsoft. Ink. Stroke](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90)) e expõe métodos e propriedades comuns para gerenciar e manipular esses traços.  O objeto [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) gerencia o tempo de vida dos traços que ele contém; o objeto [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) cria e exclui os traços que ele possui.  Cada [Microsoft. Ink. Stroke](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90)) tem um identificador que é exclusivo dentro de seu objeto pai [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) .  
  
 Na plataforma WPF, a classe <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> possui e gerencia seu próprio tempo de vida. Um grupo de objetos <xref:System.Windows.Ink.Stroke> pode ser coletado em um <xref:System.Windows.Ink.StrokeCollection>, que fornece métodos para operações comuns de gerenciamento de dados de tinta, como teste de clique, apagamento, transformação e serialização da tinta. Um <xref:System.Windows.Ink.Stroke> pode pertencer a zero, um ou mais objetos <xref:System.Windows.Ink.StrokeCollection> a qualquer momento.  Em vez de ter um objeto [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) , o <xref:System.Windows.Controls.InkCanvas> e <xref:System.Windows.Controls.InkPresenter> contêm uma <xref:System.Windows.Ink.StrokeCollection?displayProperty=nameWithType>.  
  
 O par de ilustrações a seguir compara os modelos de objeto de dados de tinta.  Nas plataformas Windows Forms e COM, o objeto [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) restringe o tempo de vida dos objetos [Microsoft. Ink. Stroke](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90)) e os pacotes da caneta pertencem aos traços individuais.  Dois ou mais traços podem referenciar o mesmo objeto [Microsoft. Ink. DrawingAttributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583636(v=vs.90)) , conforme mostrado na ilustração a seguir.  
  
 ![Diagrama do modelo de objeto de tinta para&#47;WinForms com.](./media/ink-inkownsstrokes.png "Ink_InkOwnsStrokes")  
  
 Na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], cada <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> é um objeto Common Language Runtime que existe, desde que algo tenha uma referência a ele.  Cada <xref:System.Windows.Ink.Stroke> faz referência a um objeto <xref:System.Windows.Input.StylusPointCollection> e <xref:System.Windows.Ink.DrawingAttributes?displayProperty=nameWithType>, que também são objetos Common Language Runtime.  
  
 ![Diagrama do modelo de objeto de tinta do WPF.](./media/ink-wpfinkobjectmodel.png "Ink_WPFInkObjectModel")  
  
 A tabela a seguir compara como realizar algumas tarefas comuns na plataforma WPF e nas plataformas Windows Forms e COM.  
  
|Tarefa|Windows Presentation Foundation|Windows Forms e COM|  
|----------|-------------------------------------|---------------------------|  
|Salvar tinta|<xref:System.Windows.Ink.StrokeCollection.Save%2A>|[Microsoft.Ink.Ink.Save](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571335(v=vs.90))|  
|Carregar tinta|Crie um <xref:System.Windows.Ink.StrokeCollection> com o Construtor <xref:System.Windows.Ink.StrokeCollection.%23ctor%2A>.|[Microsoft.Ink.Ink.Load](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms569609(v=vs.90))|  
|Teste de clique|<xref:System.Windows.Ink.StrokeCollection.HitTest%2A>|[Microsoft.Ink.Ink.HitTest](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571330(v=vs.90))|  
|Copiar tinta|<xref:System.Windows.Controls.InkCanvas.CopySelection%2A>|[Microsoft.Ink.Ink.ClipboardCopy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571316(v=vs.90))|  
|Colar tinta|<xref:System.Windows.Controls.InkCanvas.Paste%2A>|[Microsoft.Ink.Ink.ClipboardPaste](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571318(v=vs.90))|  
|Acessar propriedades personalizadas em uma coleção de traços|<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A> (as propriedades são armazenadas internamente e acessadas por meio de <xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>, <xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A>e <xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A>)|Usar [Microsoft. Ink. Ink. ExtendedProperties](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms582214(v=vs.90))|  
  
### <a name="sharing-ink-between-platforms"></a>Compartilhando tinta entre plataformas  
 Embora as plataformas tenham modelos de objeto diferentes para os dados de tinta, o compartilhamento de dados entre as plataformas é muito fácil. Os exemplos a seguir salva a tinta de um aplicativo Windows Forms e carregam a tinta em um aplicativo do Windows Presentation Foundation.  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#SaveWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewinforms)]
[!code-vb[WinFormWPFInk#SaveWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewinforms)]  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#LoadWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwpf)]
[!code-vb[WinFormWPFInk#LoadWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwpf)]  
  
 Os exemplos a seguir salvam a tinta de um aplicativo Windows Presentation Foundation e carregam a tinta em um aplicativo dos Windows Forms.  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#SaveWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewpf)]
[!code-vb[WinFormWPFInk#SaveWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewpf)]  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#LoadWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwinforms)]
[!code-vb[WinFormWPFInk#LoadWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwinforms)]
## <a name="events-from-the-tablet-pen"></a>Eventos da caneta eletrônica  

 O [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)), o [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))e [o Microsoft. ink. INKPICTURE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)) nas plataformas Windows Forms e com recebem eventos quando o usuário insere os dados da caneta. O [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)) ou [o Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) é anexado a uma janela ou a um controle e pode assinar os eventos gerados pelos dados de entrada do Tablet. O thread em que esses eventos ocorrem depende de se os eventos são gerados com uma caneta, um mouse ou programaticamente. Para obter mais informações sobre o uso de threads em relação a esses eventos, consulte [Considerações gerais de thread](/windows/desktop/tablet/general-threading-considerations) e [Threads nos quais um evento pode ser acionado](/windows/desktop/tablet/threads-on-which-an-event-can-fire).  
  
 Na plataforma Windows Presentation Foundation, a classe <xref:System.Windows.UIElement> tem eventos para entrada de caneta. Isso significa que cada controle expõe o conjunto completo de eventos de caneta.  Os eventos de caneta têm pares de eventos de túnel/propagação e sempre ocorrem no thread do aplicativo.  Para obter mais informações, consulte [Visão geral de eventos roteados](routed-events-overview.md).  
  
 O diagrama a seguir compara os modelos de objeto para as classes que geram eventos de caneta. O modelo de objeto do Windows Presentation Foundation mostra somente os eventos de propagação, não os equivalentes do evento de túnel.  
  
 ![Diagrama dos eventos da caneta no WPF versus WinForms.](./media/ink-stylusevents.png "Ink_StylusEvents")  
  
## <a name="pen-data"></a>Dados da caneta  
 Todas as três plataformas fornecem meios para interceptar e manipular os dados provenientes de uma caneta eletrônica.  Nas plataformas Windows Forms e COM, isso é obtido com a criação de um [Microsoft. StylusInput. RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90)), a anexação de uma janela ou controle a ele e a criação de uma classe que implementa a interface [Microsoft. StylusInput. IStylusSyncPlugin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms575201(v=vs.90)) ou [Microsoft. StylusInput. IStylusAsyncPlugin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms575194(v=vs.90)) . O plug-in personalizado é então adicionado à coleção de plug-ins do [Microsoft. StylusInput. RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90)). Para obter mais informações sobre esse modelo de objeto, consulte [Arquitetura de APIs StylusInput](/windows/desktop/tablet/architecture-of-the-stylusinput-apis).  
  
 Na plataforma WPF, a classe <xref:System.Windows.UIElement> expõe uma coleção de plug-ins, semelhante ao design para o [Microsoft. StylusInput. RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90)).  Para interceptar dados da caneta, crie uma classe que herda de <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> e adicione o objeto à coleção de <xref:System.Windows.UIElement.StylusPlugIns%2A> do <xref:System.Windows.UIElement>. Para obter mais informações sobre essa interação, consulte [Interceptando a entrada da caneta](intercepting-input-from-the-stylus.md).  
  
 Em todas as plataformas, um pool de threads recebe os dados de tinta por eventos de caneta e o envia para o thread do aplicativo.  Para obter mais informações sobre uso de threads nas plataformas Windows e COM, consulte [Considerações de thread para APIs StylusInput](/windows/desktop/tablet/threading-considerations-for-the-stylusinput-apis).  Para obter mais informações sobre uso de threads no software Windows Presentation, consulte [O modelo de threading de tinta](the-ink-threading-model.md).  
  
 A ilustração a seguir compara os modelos de objeto para as classes que recebem dados da caneta no pool de threads de caneta.  
  
 ![Diagrama do WPF do modelo StylusPlugin versus WinForms.](./media/ink-stylusplugins.png "Ink_StylusPlugins")
