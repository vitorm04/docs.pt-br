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
ms.openlocfilehash: 2ff0f134ea3174f7f034d47446aab782e2141916
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186978"
---
# <a name="scrollviewer-overview"></a>Visão geral de ScrollViewer
O conteúdo dentro de uma interface do usuário geralmente é maior do que a área de exibição de uma tela de computador. O <xref:System.Windows.Controls.ScrollViewer> controle fornece uma maneira conveniente de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] permitir a rolagem de conteúdo em aplicativos. Este tópico introduz <xref:System.Windows.Controls.ScrollViewer> o elemento e fornece vários exemplos de uso.  
  
<a name="what_is_a_scrollviewer_element"></a>
## <a name="the-scrollviewer-control"></a>O controle ScrollViewer  
 Existem dois elementos predefinidos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que <xref:System.Windows.Controls.Primitives.ScrollBar> permitem <xref:System.Windows.Controls.ScrollViewer>a rolagem em aplicativos: e . O <xref:System.Windows.Controls.ScrollViewer> controle encapsula elementos <xref:System.Windows.Controls.Primitives.ScrollBar> horizontais e verticais e um recipiente de conteúdo (como um <xref:System.Windows.Controls.Panel> elemento) a fim de exibir outros elementos visíveis em uma área rolável. Você deve construir um objeto personalizado <xref:System.Windows.Controls.Primitives.ScrollBar> para usar o elemento para rolagem de conteúdo. No entanto, <xref:System.Windows.Controls.ScrollViewer> você pode usar o elemento por si só porque é um controle composto que encapsula a <xref:System.Windows.Controls.Primitives.ScrollBar> funcionalidade.  
  
 O <xref:System.Windows.Controls.ScrollViewer> controle responde aos comandos do mouse e do teclado e define inúmeros métodos com os quais rolar conteúdo por incrementos predeterminados. Você pode <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> usar o evento para <xref:System.Windows.Controls.ScrollViewer> detectar uma alteração em um estado.  
  
 Um <xref:System.Windows.Controls.ScrollViewer> só pode ter um <xref:System.Windows.Controls.Panel> filho, tipicamente <xref:System.Windows.Controls.Panel.Children%2A> um elemento que pode hospedar uma coleção de elementos. A <xref:System.Windows.Controls.ContentPresenter.Content%2A> propriedade define o único <xref:System.Windows.Controls.ScrollViewer>filho do .  
  
<a name="scrollviewer_physical_vs_logical"></a>
## <a name="physical-vs-logical-scrolling"></a>Rolagem física vs. Lógica  
 Rolagem física é usada para rolar conteúdo por um incremento físico predeterminado, geralmente por um valor declarado em pixels. Rolagem lógica é usada para rolar para o próximo item na árvore lógica. Rolagem física é o comportamento <xref:System.Windows.Controls.Panel> padrão de rolagem para a maioria dos elementos. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dá suporte a ambos os tipos de rolagem.  
  
#### <a name="the-iscrollinfo-interface"></a>A interface IScrollInfo  
 A <xref:System.Windows.Controls.Primitives.IScrollInfo> interface representa a região principal <xref:System.Windows.Controls.ScrollViewer> de rolagem dentro de um controle ou derivado. A interface define propriedades de rolagem e <xref:System.Windows.Controls.Panel> métodos que podem ser implementados por elementos que requerem rolagem por unidade lógica, em vez de por um incremento físico. Lançar uma <xref:System.Windows.Controls.Primitives.IScrollInfo> instância de <xref:System.Windows.Controls.Panel> um derivado e, em seguida, usando seus métodos de rolagem fornece uma maneira útil de rolar para a próxima unidade lógica em uma coleção de crianças, em vez de por incremento de pixel. Por padrão, <xref:System.Windows.Controls.ScrollViewer> o controle suporta rolagem por unidades físicas.  
  
 <xref:System.Windows.Controls.StackPanel>e <xref:System.Windows.Controls.VirtualizingStackPanel> ambos <xref:System.Windows.Controls.Primitives.IScrollInfo> implementam e suportam nativamente rolagem lógica. Para controles de layout que suportam nativamente rolagem lógica, você <xref:System.Windows.Controls.Panel> ainda <xref:System.Windows.Controls.ScrollViewer> pode obter <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> rolagem física envolvendo o elemento host em um e definindo a propriedade para `false`.  
  
 O exemplo de código a seguir <xref:System.Windows.Controls.Primitives.IScrollInfo> demonstra <xref:System.Windows.Controls.StackPanel> como lançar uma instância<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>de a e usar métodos de rolagem de conteúdo ( e ) definidos pela interface.  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>
## <a name="defining-and-using-a-scrollviewer-element"></a>Definindo e usando um elemento ScrollViewer  
 O exemplo a <xref:System.Windows.Controls.ScrollViewer> seguir cria um em uma janela que contém algum texto e um retângulo. <xref:System.Windows.Controls.Primitives.ScrollBar>elementos aparecem apenas quando são necessários. Quando você redimensiona <xref:System.Windows.Controls.Primitives.ScrollBar> a janela, os elementos aparecem <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> e desaparecem, devido aos valores atualizados das propriedades e.  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>
## <a name="styling-a-scrollviewer"></a>Aplicando estilo a um ScrollViewer  
 Como todos os controles no <xref:System.Windows.Controls.ScrollViewer> Windows Presentation Foundation, o pode ser estilizado para alterar o comportamento de renderização padrão do controle. Para obter informações adicionais sobre aplicação de estilo de controle, consulte [Aplicação de estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>
## <a name="paginating-documents"></a>Paginando documentos  
 Para o conteúdo do documento, uma alternativa à rolagem é escolher um contêiner de documento que dá suporte à paginação. <xref:System.Windows.Documents.FlowDocument>é para documentos que foram projetados para serem <xref:System.Windows.Controls.FlowDocumentPageViewer>hospedados dentro de um controle de visualização, como, que suporta paginar conteúdo em várias páginas, impedindo a necessidade de rolagem. <xref:System.Windows.Controls.DocumentViewer>fornece uma solução <xref:System.Windows.Documents.FixedDocument> para visualização de conteúdo, que usa rolagem tradicional para exibir conteúdo fora do reino da área de exibição.  
  
 Para obter informações adicionais sobre formatos de documento e opções de apresentação, consulte [Documentos no WPF](../advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [Como: Criar um Visualizador de Pergaminho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [Documentos no WPF](../advanced/documents-in-wpf.md)
- [Estilos e modelos ScrollBar](scrollbar-styles-and-templates.md)
- [Controles](../advanced/optimizing-performance-controls.md)
