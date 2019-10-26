---
title: Como associar a XDocument, XElement ou LINQ para resultados de consulta XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
ms.openlocfilehash: 070f67f30613d4522a48e08fd1c208fbe5887525
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920117"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a>Como associar a XDocument, XElement ou LINQ para resultados de consulta XML

Este exemplo demonstra como associar dados XML a um <xref:System.Windows.Controls.ItemsControl> usando <xref:System.Xml.Linq.XDocument>.

## <a name="example"></a>Exemplo

O código XAML a seguir define um <xref:System.Windows.Controls.ItemsControl> e inclui um modelo de dados para dados do tipo `Planet` no namespace XML `http://planetsNS`. Um tipo de dados XML que ocupa um namespace deve incluir o namespace entre chaves e, se ele aparecer onde uma extensão de marcação XAML pode aparecer, deverá preceder o namespace com uma sequência de escape de chave. Esse código é associado a propriedades dinâmicas que correspondem aos métodos <xref:System.Xml.Linq.XContainer.Element%2A> e <xref:System.Xml.Linq.XElement.Attribute%2A> da classe <xref:System.Xml.Linq.XElement>. As propriedades dinâmicas permitem que o XAML se associe a propriedades dinâmicas que compartilham os nomes dos métodos. Para saber mais, confira [LINQ to XML propriedades dinâmicas](linq-to-xml-dynamic-properties.md). Veja como a declaração de namespace padrão para o XML não se aplica aos nomes de atributos.

[!code-xaml[XLinqExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]
[!code-xaml[XLinqExample#ItemsControl](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]

O código C# a seguir chama<xref:System.Xml.Linq.XDocument.Load%2A>e define o contexto de dados do painel de pilha para todos os subelementos do elemento nomeado`SolarSystemPlanets`no namespace XML`http://planetsNS`.

[!code-csharp[XLinqExample#LoadDCFromFile](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
[!code-vb[XLinqExample#LoadDCFromFile](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]

Os dados XML podem ser armazenados como um recurso XAML usando <xref:System.Windows.Data.ObjectDataProvider>. Para obter um exemplo completo, consulte [código-fonte L2DBForm. XAML](l2dbform-xaml-source-code.md). O exemplo a seguir mostra como o código pode definir o contexto de dados para um recurso de objeto.

[!code-csharp[XLinqExample#LoadDCFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
[!code-vb[XLinqExample#LoadDCFromXAML](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]

As propriedades dinâmicas que são mapeadas para <xref:System.Xml.Linq.XContainer.Element%2A> e <xref:System.Xml.Linq.XElement.Attribute%2A> fornecem flexibilidade no XAML. O código também pode se associar aos resultados de um LINQ para consulta XML. Este exemplo se associa aos resultados da consulta ordenados por um valor de elemento.

[!code-csharp[XLinqExample#BindToResults](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
[!code-vb[XLinqExample#BindToResults](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]

## <a name="see-also"></a>Consulte também

- [Visão geral das origens da associação](binding-sources-overview.md)
- [Visão geral da vinculação de dados do WPF com LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md)
- [Vinculação de dados de WPF usando o exemplo LINQ to XML](linq-to-xml-data-binding-sample.md)
- [Propriedades dinâmicas LINQ to XML](linq-to-xml-dynamic-properties.md)
