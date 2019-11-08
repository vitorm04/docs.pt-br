---
title: Como disponibilizar dados para associação em XAML
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 97e878e4932ca9122bf27f76c32d1a56e69f253a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740599"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Como disponibilizar dados para associação em XAML
Este tópico discute várias maneiras de disponibilizar dados para associação em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], dependendo das necessidades do seu aplicativo.  
  
## <a name="example"></a>Exemplo  
 Se você tiver um objeto Common Language Runtime (CLR) ao qual deseja associar-se [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], uma maneira de tornar o objeto disponível para associação é defini-lo como um recurso e fornecê-lo a um `x:Key`. No exemplo a seguir, temos um objeto `Person` com uma propriedade de cadeia de caracteres denominada `PersonName`. O objeto `Person` (na linha mostrado realçado que contém o elemento `<src>`) é definido no namespace chamado `SDKSample`.  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Em seguida, você pode associar o controle de <xref:System.Windows.Controls.TextBlock> ao objeto em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], como a linha realçada que contém o elemento `<TextBlock>` mostra. 
  
 Como alternativa, você pode usar a classe <xref:System.Windows.Data.ObjectDataProvider>, como no exemplo a seguir:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Você define a associação da mesma maneira, como a linha realçada que contém o elemento `<TextBlock>` mostra.  
  
 Neste exemplo específico, o resultado é o mesmo: você tem um <xref:System.Windows.Controls.TextBlock> com o conteúdo de texto `Joe`. No entanto, a classe <xref:System.Windows.Data.ObjectDataProvider> fornece funcionalidade como a capacidade de associar ao resultado de um método. Você pode optar por usar a classe <xref:System.Windows.Data.ObjectDataProvider> se precisar da funcionalidade que ela fornece.  
  
 No entanto, se estiver associando a um objeto que já foi criado, será necessário definir o `DataContext` no código, como no exemplo a seguir.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Para acessar dados XML para associação usando a classe <xref:System.Windows.Data.XmlDataProvider>, consulte [associar dados XML usando um XmlDataProvider e consultas XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Para acessar dados XML para associação usando a classe <xref:System.Windows.Data.ObjectDataProvider>, consulte [associar a resultados de consulta de XDocument, XElement ou LINQ for XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Para obter informações sobre várias maneiras que você pode especificar os dados aos quais você está ligando, consulte [especificar a origem da Associação](how-to-specify-the-binding-source.md). Para obter informações sobre quais tipos de dados você pode associar ou como implementar seus próprios objetos Common Language Runtime (CLR) para associação, consulte [visão geral de fontes de associação](binding-sources-overview.md).  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
