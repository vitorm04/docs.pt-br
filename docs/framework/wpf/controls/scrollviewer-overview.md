---
title: Visão geral de ScrollViewer
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
ms.openlocfilehash: 1797f956ec41ba085dee7e1cb11a3129004552b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="scrollviewer-overview"></a>Visão geral de ScrollViewer
O conteúdo dentro de uma interface do usuário geralmente é maior do que a área de exibição de uma tela de computador. O <xref:System.Windows.Controls.ScrollViewer> controle fornece uma maneira conveniente para habilitar a rolagem do conteúdo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplicativos. Este tópico apresenta o <xref:System.Windows.Controls.ScrollViewer> elemento e fornece vários exemplos de uso.  
  
<a name="what_is_a_scrollviewer_element"></a>   
## <a name="the-scrollviewer-control"></a>O controle ScrollViewer  
 Há dois elementos predefinidos que permitem a rolagem em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos: <xref:System.Windows.Controls.Primitives.ScrollBar> e <xref:System.Windows.Controls.ScrollViewer>. O <xref:System.Windows.Controls.ScrollViewer> controle encapsula horizontal e vertical <xref:System.Windows.Controls.Primitives.ScrollBar> elementos e um recipiente de conteúdo (como um <xref:System.Windows.Controls.Panel> elemento) para exibir outros elementos visíveis em uma área rolável. Você deve criar um objeto personalizado para usar o <xref:System.Windows.Controls.Primitives.ScrollBar> elemento para rolagem de conteúdo. No entanto, você pode usar o <xref:System.Windows.Controls.ScrollViewer> elemento por si só, porque ele é um controle composto que encapsula <xref:System.Windows.Controls.Primitives.ScrollBar> funcionalidade.  
  
 O <xref:System.Windows.Controls.ScrollViewer> controle responde aos comandos do mouse e teclado e define vários métodos com a qual Role o conteúdo em incrementos predeterminados. Você pode usar o <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> eventos para detectar uma alteração em um <xref:System.Windows.Controls.ScrollViewer> estado.  
  
 Um <xref:System.Windows.Controls.ScrollViewer> só pode ter um filho, geralmente um <xref:System.Windows.Controls.Panel> elemento que pode hospedar um <xref:System.Windows.Controls.Panel.Children%2A> coleção de elementos. O <xref:System.Windows.Controls.ContentPresenter.Content%2A> propriedade define o único filho do <xref:System.Windows.Controls.ScrollViewer>.  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## <a name="physical-vs-logical-scrolling"></a>Rolagem física vs. lógica  
 Rolagem física é usada para rolar conteúdo por um incremento físico predeterminado, geralmente por um valor declarado em pixels. Rolagem lógica é usada para rolar para o próximo item na árvore lógica. Rolagem física é o comportamento padrão de rolagem para a maioria dos <xref:System.Windows.Controls.Panel> elementos. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dá suporte a ambos os tipos de rolagem.  
  
#### <a name="the-iscrollinfo-interface"></a>A interface IScrollInfo  
 O <xref:System.Windows.Controls.Primitives.IScrollInfo> interface representa a área de rolagem principal em um <xref:System.Windows.Controls.ScrollViewer> ou controle derivado. A interface define propriedades e métodos que podem ser implementados por rolagem <xref:System.Windows.Controls.Panel> elementos que requerem a rolagem por unidade lógica, em vez de um incremento físico. Conversão de uma instância de <xref:System.Windows.Controls.Primitives.IScrollInfo> para um derivado <xref:System.Windows.Controls.Panel> e, em seguida, usar seus métodos de rolagem fornece uma maneira útil de rolar para a próxima unidade lógica em uma coleção de filhos, e não por incremento de pixel. Por padrão, o <xref:System.Windows.Controls.ScrollViewer> controle oferece suporte a rolagem por unidades físicas.  
  
 <xref:System.Windows.Controls.StackPanel> e <xref:System.Windows.Controls.VirtualizingStackPanel> ambos implementam <xref:System.Windows.Controls.Primitives.IScrollInfo> e suporte nativo a rolagem lógica. Para controles de layout que nativamente suporte rolagem lógica, você ainda pode obter rolagem física encapsulando host <xref:System.Windows.Controls.Panel> elemento em um <xref:System.Windows.Controls.ScrollViewer> e configuração o <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> propriedade `false`.  
  
 O exemplo de código a seguir demonstra como converter uma instância de <xref:System.Windows.Controls.Primitives.IScrollInfo> para um <xref:System.Windows.Controls.StackPanel> e usar os métodos de rolagem de conteúdo (<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> e <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>) definidos pela interface.  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## <a name="defining-and-using-a-scrollviewer-element"></a>Definindo e usando um elemento ScrollViewer  
 O exemplo a seguir cria um <xref:System.Windows.Controls.ScrollViewer> em uma janela que contém algum texto e um retângulo. <xref:System.Windows.Controls.Primitives.ScrollBar> os elementos aparecem somente quando são necessários. Quando você redimensiona a janela, o <xref:System.Windows.Controls.Primitives.ScrollBar> elementos aparecem e desaparecem, devido a valores atualizados do <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> e <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> propriedades.  
  
 [!code-cpp[ScrollViewer#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## <a name="styling-a-scrollviewer"></a>Aplicando estilo a um ScrollViewer  
 Como todos os controles no Windows Presentation Foundation, o <xref:System.Windows.Controls.ScrollViewer> pode ser estilizado para alterar o comportamento de renderização padrão do controle. Para obter informações adicionais sobre aplicação de estilo de controle, consulte [Aplicação de estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## <a name="paginating-documents"></a>Paginando documentos  
 Para o conteúdo do documento, uma alternativa à rolagem é escolher um contêiner de documento que dá suporte à paginação. <xref:System.Windows.Documents.FlowDocument> para documentos que são projetados para ser hospedado em um controle de exibição, como <xref:System.Windows.Controls.FlowDocumentPageViewer>, que oferece suporte à paginação de conteúdo em várias páginas, evitando a necessidade de rolagem. <xref:System.Windows.Controls.DocumentViewer> Fornece uma solução para exibição <xref:System.Windows.Documents.FixedDocument> conteúdo, que usa rolagem tradicional para exibir o conteúdo fora do realm da área de exibição.  
  
 Para obter informações adicionais sobre formatos de documento e opções de apresentação, consulte [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.ScrollBar>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 [Criar um visualizador de rolagem](http://msdn.microsoft.com/library/c8e46af7-b417-441b-aa30-791cbdbd43ef)  
 [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Estilos e modelos ScrollBar](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)  
 [Controles](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
