---
title: 'Como: Associar dados XML usando um XMLDataProvider e consultas XPath'
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: dc4fb2d5f0c48c077d2ff7ca5e5269ce5cba71e5
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400491"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Como: Associar dados XML usando um XMLDataProvider e consultas XPath
Este exemplo mostra como associar [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] dados usando um. <xref:System.Windows.Data.XmlDataProvider>  
  
 Com um <xref:System.Windows.Data.XmlDataProvider>, os dados subjacentes que podem ser acessados por meio da ligação de dados em seu [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] aplicativo podem ser qualquer árvore de nós. Em outras palavras, um <xref:System.Windows.Data.XmlDataProvider> fornece uma maneira conveniente de usar qualquer árvore de [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] nós como uma fonte de associação.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, os dados são inseridos diretamente como [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] uma <xref:System.Windows.FrameworkElement.Resources%2A> *ilha de dados* na seção. Uma ilha de dados [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deve ser encapsulada em marcas `<x:XData>` e sempre ter um único nó raiz, que é *Inventário*, neste exemplo.  
  
> [!NOTE]
>  O nó raiz dos dados [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] tem um atributo **xmlns** que define o namespace [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] para uma cadeia de caracteres vazia. Esse é um requisito para aplicar consultas XPath a uma ilha de dados embutida na página [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Nesse caso embutido, o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]e, portanto, a ilha de dados, <xref:System.Windows> herda o namespace. Por isso, você precisa definir o namespace em branco para impedir que as consultas XPath sejam qualificadas pelo <xref:System.Windows> namespace, o que indiretoia as consultas.  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Conforme mostrado neste exemplo, para criar a mesma declaração de associação na sintaxe do atributo, você precisa fazer o escape de caracteres especiais corretamente. Para obter mais informações, consulte [Entidades de caractere XML e XAML](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 O <xref:System.Windows.Controls.ListBox> exibirá os itens a seguir quando este exemplo for executado. Esses são os *Título*s de todos os elementos em *Livros* com um valor de *Estoque* de "*sem*" ou um valor de *Número* de 3 ou maior ou igual a 8. Observe que nenhum item de *CD* é retornado porque <xref:System.Windows.Data.XmlDataProvider.XPath%2A> o <xref:System.Windows.Data.XmlDataProvider> valor definido no indica que somente os  elementos Books devem ser expostos (essencialmente definindo um filtro).  
  
 ![Captura de tela do exemplo XPath mostrando o título de quatro livros.](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 Neste exemplo, os títulos de livros são exibidos porque o <xref:System.Windows.Data.Binding.XPath%2A> <xref:System.Windows.Controls.TextBlock> da associação no <xref:System.Windows.DataTemplate> é definido como "*title*". Se você quiser exibir o valor de um atributo, como o *ISBN*, você definiria esse <xref:System.Windows.Data.Binding.XPath%2A> valor como "`@ISBN`".  
  
 As propriedades **XPath** no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são manipuladas pelo método XmlNode.SelectNodes. Você pode modificar as consultas **XPath** para obter resultados diferentes. Aqui estão alguns exemplos para a <xref:System.Windows.Data.Binding.XPath%2A> consulta no associado <xref:System.Windows.Controls.ListBox> do exemplo anterior:  
  
- O `XPath="Book[1]"` retornará o primeiro elemento de livro ("XML in Action"). Observe que os índices **XPath** são baseados em 1, e não em 0.  
  
- O `XPath="Book[@*]"` retornará todos os elementos de livro com quaisquer atributos.  
  
- O `XPath="Book[last()-1]"` retornará do segundo ao último elemento de livro ("Introducing Microsoft .NET").  
  
- O `XPath="*[position()>3]"` retornará todos os elementos de livro exceto os três primeiros.  
  
 Quando você executa uma consulta **XPath** , ela retorna um <xref:System.Xml.XmlNode> ou uma lista de XMLNodes. <xref:System.Xml.XmlNode>é um objeto Common Language Runtime (CLR), o que significa que você pode <xref:System.Windows.Data.Binding.Path%2A> usar a propriedade para associar às propriedades de Common Language Runtime (CLR). Considere o exemplo anterior novamente. Se o restante do exemplo permanecer o mesmo e você alterar a <xref:System.Windows.Controls.TextBlock> Associação para o seguinte, você verá os nomes dos XMLNodes retornados <xref:System.Windows.Controls.ListBox>no. Nesse caso, o nome de todos os nós retornados é "*Livro*".  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 Em alguns aplicativos, inserir o [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] como uma ilha de dados na fonte da página [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pode ser inconveniente, pois o conteúdo exato dos dados deve ser conhecido no tempo de compilação. Portanto, também há suporte para obter os dados de um arquivo [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] externo, como no exemplo a seguir:  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Se os [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados residirem em um arquivo remoto [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] , você definirá o acesso aos dados atribuindo um apropriado [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] ao atributo da <xref:System.Windows.Data.XmlDataProvider.Source%2A> seguinte maneira:  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Data.ObjectDataProvider>
- [Associar a XDocument, XElement ou LINQ para resultados de consulta XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)
- [Usar o padrão de detalhes mestre com os dados XML hierárquicos](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Visão geral das origens da associação](binding-sources-overview.md)
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Tópicos de instruções](data-binding-how-to-topics.md)
