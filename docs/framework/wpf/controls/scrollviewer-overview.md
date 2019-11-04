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
ms.openlocfilehash: 993f3c861cbead88df3503eb01f18e5d1f69e2d8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458427"
---
# <a name="scrollviewer-overview"></a>Visão geral de ScrollViewer
O conteúdo dentro de uma interface do usuário geralmente é maior do que a área de exibição de uma tela de computador. O controle de <xref:System.Windows.Controls.ScrollViewer> fornece uma maneira conveniente de habilitar a rolagem de conteúdo em aplicativos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Este tópico apresenta o elemento <xref:System.Windows.Controls.ScrollViewer> e fornece vários exemplos de uso.  
  
<a name="what_is_a_scrollviewer_element"></a>   
## <a name="the-scrollviewer-control"></a>O controle ScrollViewer  
 Há dois elementos predefinidos que permitem a rolagem em aplicativos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: <xref:System.Windows.Controls.Primitives.ScrollBar> e <xref:System.Windows.Controls.ScrollViewer>. O controle de <xref:System.Windows.Controls.ScrollViewer> encapsula elementos de <xref:System.Windows.Controls.Primitives.ScrollBar> horizontais e verticais e um contêiner de conteúdo (como um elemento <xref:System.Windows.Controls.Panel>) a fim de exibir outros elementos visíveis em uma área rolável. Você deve criar um objeto personalizado para usar o elemento <xref:System.Windows.Controls.Primitives.ScrollBar> para a rolagem de conteúdo. No entanto, você pode usar o elemento <xref:System.Windows.Controls.ScrollViewer> por si só porque ele é um controle composto que encapsula <xref:System.Windows.Controls.Primitives.ScrollBar> funcionalidade.  
  
 O controle de <xref:System.Windows.Controls.ScrollViewer> responde a comandos do mouse e do teclado e define vários métodos com os quais rolar o conteúdo por incrementos predeterminados. Você pode usar o evento <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> para detectar uma alteração em um estado de <xref:System.Windows.Controls.ScrollViewer>.  
  
 Uma <xref:System.Windows.Controls.ScrollViewer> só pode ter um filho, normalmente um elemento <xref:System.Windows.Controls.Panel> que pode hospedar uma <xref:System.Windows.Controls.Panel.Children%2A> coleção de elementos. A propriedade <xref:System.Windows.Controls.ContentPresenter.Content%2A> define o único filho da <xref:System.Windows.Controls.ScrollViewer>.  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## <a name="physical-vs-logical-scrolling"></a>Rolagem física versus lógica  
 Rolagem física é usada para rolar conteúdo por um incremento físico predeterminado, geralmente por um valor declarado em pixels. Rolagem lógica é usada para rolar para o próximo item na árvore lógica. A rolagem física é o comportamento de rolagem padrão para a maioria dos elementos <xref:System.Windows.Controls.Panel>. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dá suporte a ambos os tipos de rolagem.  
  
#### <a name="the-iscrollinfo-interface"></a>A interface IScrollInfo  
 A interface <xref:System.Windows.Controls.Primitives.IScrollInfo> representa a região de rolagem principal dentro de um <xref:System.Windows.Controls.ScrollViewer> ou controle derivado. A interface define propriedades e métodos de rolagem que podem ser implementados por <xref:System.Windows.Controls.Panel> elementos que exigem a rolagem por unidade lógica, em vez de um incremento físico. Converter uma instância de <xref:System.Windows.Controls.Primitives.IScrollInfo> em um <xref:System.Windows.Controls.Panel> derivado e, em seguida, usar seus métodos de rolagem fornece uma maneira útil de rolar para a próxima unidade lógica em uma coleção filho, em vez de por incremento de pixel. Por padrão, o controle de <xref:System.Windows.Controls.ScrollViewer> dá suporte à rolagem por unidades físicas.  
  
 <xref:System.Windows.Controls.StackPanel> e <xref:System.Windows.Controls.VirtualizingStackPanel> implementam <xref:System.Windows.Controls.Primitives.IScrollInfo> e oferecem suporte nativo à rolagem lógica. Para controles de layout que dão suporte nativo à rolagem lógica, você ainda pode obter a rolagem física encapsulando o elemento de <xref:System.Windows.Controls.Panel> do host em um <xref:System.Windows.Controls.ScrollViewer> e definindo a propriedade <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> como `false`.  
  
 O exemplo de código a seguir demonstra como converter uma instância de <xref:System.Windows.Controls.Primitives.IScrollInfo> em um <xref:System.Windows.Controls.StackPanel> e usar os métodos de rolagem de conteúdo (<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> e <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>) definidos pela interface.  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## <a name="defining-and-using-a-scrollviewer-element"></a>Definindo e usando um elemento ScrollViewer  
 O exemplo a seguir cria um <xref:System.Windows.Controls.ScrollViewer> em uma janela que contém texto e um retângulo. <xref:System.Windows.Controls.Primitives.ScrollBar> elementos aparecem apenas quando são necessários. Quando você redimensiona a janela, os elementos de <xref:System.Windows.Controls.Primitives.ScrollBar> aparecem e desaparecem, devido aos valores atualizados das propriedades <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> e <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A>.  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## <a name="styling-a-scrollviewer"></a>Aplicando estilo a um ScrollViewer  
 Como todos os controles em Windows Presentation Foundation, o <xref:System.Windows.Controls.ScrollViewer> pode ser estilizado para alterar o comportamento de renderização padrão do controle. Para obter informações adicionais sobre aplicação de estilo de controle, consulte [Aplicação de estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## <a name="paginating-documents"></a>Paginando documentos  
 Para o conteúdo do documento, uma alternativa à rolagem é escolher um contêiner de documento que dá suporte à paginação. <xref:System.Windows.Documents.FlowDocument> é para documentos que são projetados para serem hospedados em um controle de exibição, como <xref:System.Windows.Controls.FlowDocumentPageViewer>, que dá suporte à paginação de conteúdo em várias páginas, evitando a necessidade de rolagem. <xref:System.Windows.Controls.DocumentViewer> fornece uma solução para exibir <xref:System.Windows.Documents.FixedDocument> conteúdo, que usa a rolagem tradicional para exibir o conteúdo fora do Realm da área de exibição.  
  
 Para obter informações adicionais sobre formatos de documento e opções de apresentação, consulte [Documentos no WPF](../advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [Como: criar um visualizador de rolagem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [Documentos no WPF](../advanced/documents-in-wpf.md)
- [Estilos e modelos ScrollBar](scrollbar-styles-and-templates.md)
- [Controles](../advanced/optimizing-performance-controls.md)
