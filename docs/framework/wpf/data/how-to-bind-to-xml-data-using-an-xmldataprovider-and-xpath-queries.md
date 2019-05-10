---
title: 'Como: Associar dados XML usando um XMLDataProvider e consultas XPath'
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: 49f32ae4f358885268044cbfd785239f537940ae
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609413"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Como: Associar dados XML usando um XMLDataProvider e consultas XPath
Este exemplo mostra como associar a [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] dados usando um <xref:System.Windows.Data.XmlDataProvider>.  
  
 Com um <xref:System.Windows.Data.XmlDataProvider>, os dados subjacentes que podem ser acessados por meio da vinculação de dados em seu aplicativo podem ser qualquer árvore de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] nós. Em outras palavras, uma <xref:System.Windows.Data.XmlDataProvider> fornece uma maneira conveniente de utilizar qualquer árvore de [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] nós como uma origem da associação.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, os dados são inseridos diretamente como um [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] *ilha de dados* dentro de <xref:System.Windows.FrameworkElement.Resources%2A> seção. Uma ilha de dados [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deve ser encapsulada em marcas `<x:XData>` e sempre ter um único nó raiz, que é *Inventário*, neste exemplo.  
  
> [!NOTE]
>  O nó raiz dos dados [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] tem um atributo **xmlns** que define o namespace [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] para uma cadeia de caracteres vazia. Esse é um requisito para aplicar consultas XPath a uma ilha de dados embutida na página [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. No caso embutido, o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], e, portanto, a ilha de dados herda o <xref:System.Windows> namespace. Por isso, você precisa definir o namespace em branco para manter as consultas XPath sejam qualificadas pelo <xref:System.Windows> namespace, o que direcionaria as consultas.  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Conforme mostrado neste exemplo, para criar a mesma declaração de associação na sintaxe do atributo, você precisa fazer o escape de caracteres especiais corretamente. Para obter mais informações, consulte [Entidades de caractere XML e XAML](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 O <xref:System.Windows.Controls.ListBox> mostrará os itens a seguir quando este exemplo é executado. Esses são os *Título*s de todos os elementos em *Livros* com um valor de *Estoque* de "*sem*" ou um valor de *Número* de 3 ou maior ou igual a 8. Observe que nenhum *CD* é retornado porque o <xref:System.Windows.Data.XmlDataProvider.XPath%2A> conjunto de valores a <xref:System.Windows.Data.XmlDataProvider> indica que apenas o *manuais* elementos devem ser expostos (essencialmente Configurando um filtro).  
  
 ![Captura de tela do XPath de exemplo que mostra o título de quatro livros.](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 Neste exemplo, os títulos de livro são exibidos porque o <xref:System.Windows.Data.Binding.XPath%2A> do <xref:System.Windows.Controls.TextBlock> de associação na <xref:System.Windows.DataTemplate> é definido como "*título*". Se você deseja exibir o valor de um atributo, como o *ISBN*, você definiria aquele <xref:System.Windows.Data.Binding.XPath%2A> de valor para "`@ISBN`".  
  
 As propriedades **XPath** no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são manipuladas pelo método XmlNode.SelectNodes. Você pode modificar as consultas **XPath** para obter resultados diferentes. Aqui estão alguns exemplos para o <xref:System.Windows.Data.Binding.XPath%2A> o limite de consulta <xref:System.Windows.Controls.ListBox> do exemplo anterior:  
  
- O `XPath="Book[1]"` retornará o primeiro elemento de livro ("XML in Action"). Observe que os índices **XPath** são baseados em 1, e não em 0.  
  
- O `XPath="Book[@*]"` retornará todos os elementos de livro com quaisquer atributos.  
  
- O `XPath="Book[last()-1]"` retornará do segundo ao último elemento de livro ("Introducing Microsoft .NET").  
  
- O `XPath="*[position()>3]"` retornará todos os elementos de livro exceto os três primeiros.  
  
 Quando você executa um **XPath** consultar, ele retorna um <xref:System.Xml.XmlNode> ou uma lista de XmlNodes. <xref:System.Xml.XmlNode> é um [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objeto, o que significa que você pode usar o <xref:System.Windows.Data.Binding.Path%2A> propriedade se associar a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] propriedades. Considere o exemplo anterior novamente. Se o restante do exemplo permanece a mesma e alterar o <xref:System.Windows.Controls.TextBlock> associação a seguir, você verá os nomes dos XmlNodes retornados no <xref:System.Windows.Controls.ListBox>. Nesse caso, o nome de todos os nós retornados é "*Livro*".  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 Em alguns aplicativos, inserir o [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] como uma ilha de dados na fonte da página [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pode ser inconveniente, pois o conteúdo exato dos dados deve ser conhecido no tempo de compilação. Portanto, também há suporte para obter os dados de um arquivo [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] externo, como no exemplo a seguir:  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Se o [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados residem em um controle remoto [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] arquivo, você definiria acesso aos dados por meio da atribuição apropriado [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] para o <xref:System.Windows.Data.XmlDataProvider.Source%2A> atributo da seguinte maneira:  
  
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
