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
ms.openlocfilehash: 7e4f9cc2f5e6815a35b4911f5b4a480161d66ef3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556686"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a>Como associar a XDocument, XElement ou LINQ para resultados de consulta XML
Este exemplo demonstra como associar dados XML em uma <xref:System.Windows.Controls.ItemsControl> usando <xref:System.Xml.Linq.XDocument>.  
  
## <a name="example"></a>Exemplo  
 O código XAML a seguir define uma <xref:System.Windows.Controls.ItemsControl> e inclui um modelo de dados para o tipo de dados `Planet` no `http://planetsNS` namespace XML. Um tipo de dados XML que ocupa um namespace deve incluir o namespace entre chaves e, se ele aparecer onde uma extensão de marcação XAML pode aparecer, deverá preceder o namespace com uma sequência de escape de chave. Esse código associa a propriedades dinâmicas que correspondem do <xref:System.Xml.Linq.XContainer.Element%2A> e <xref:System.Xml.Linq.XElement.Attribute%2A> métodos do <xref:System.Xml.Linq.XElement> classe. As propriedades dinâmicas permitem que o XAML se associe a propriedades dinâmicas que compartilham os nomes dos métodos. Para saber mais, consulte [Propriedades Dinâmicas LINQ to XML](/visualstudio/designers/linq-to-xml-dynamic-properties). Veja como a declaração de namespace padrão para o XML não se aplica aos nomes de atributos.  
  
 [!code-xaml[XLinqExample#StackPanelResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xaml[XLinqExample#ItemsControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 As seguintes chamadas de código em c# <xref:System.Xml.Linq.XDocument.Load%2A> e define o contexto de dados do painel de pilha para todos os subelementos do elemento chamado `SolarSystemPlanets` no `http://planetsNS` namespace XML.  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 Dados XML podem ser armazenados como um recurso XAML usando <xref:System.Windows.Data.ObjectDataProvider>. Para um exemplo completo, consulte [Código-fonte L2DBForm.xaml](http://msdn.microsoft.com/library/624e96d4-6d27-4195-8ac2-2f3835f6c57e). O exemplo a seguir mostra como o código pode definir o contexto de dados para um recurso de objeto.  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 As propriedades dinâmicas que mapeiam para <xref:System.Xml.Linq.XContainer.Element%2A> e <xref:System.Xml.Linq.XElement.Attribute%2A> fornecem flexibilidade em XAML. O código também pode se associar aos resultados de um LINQ para consulta XML. Este exemplo se associa aos resultados da consulta ordenados por um valor de elemento.  
  
 [!code-csharp[XLinqExample#BindToResults](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral das origens da associação](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [Visão geral da vinculação de dados do WPF com LINQ to XML](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)  
 [Vinculação de dados de WPF usando o exemplo LINQ to XML](/visualstudio/designers/wpf-data-binding-using-linq-to-xml-example)  
 [Propriedades dinâmicas LINQ to XML](/visualstudio/designers/linq-to-xml-dynamic-properties)
