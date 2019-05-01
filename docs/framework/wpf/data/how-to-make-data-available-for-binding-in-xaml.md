---
title: 'Como: Disponibilizar dados para associação em XAML'
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 2d51f06da31482c46b04d1eb86172c3eda246c20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010300"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Como: Disponibilizar dados para associação em XAML
Este tópico discute várias maneiras que você pode tornar dados disponíveis para associação em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], dependendo das necessidades do seu aplicativo.  
  
## <a name="example"></a>Exemplo  
 Se você tiver um objeto [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] que deseja associar de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], uma maneira de disponibilizar o objeto para associação será defini-lo como um recurso e conceder um `x:Key` a ele. No exemplo a seguir, temos um objeto `Person` com uma propriedade de cadeia de caracteres denominada `PersonName`. O `Person` objeto (na linha mostrada realçada que contém o `<src>` elemento) é definido no namespace chamado `SDKSample`.  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Em seguida, você pode associar o <xref:System.Windows.Controls.TextBlock> controle para o objeto no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], como a linha destacada, que contém o `<TextBlock>` mostra do elemento. 
  
 Como alternativa, você pode usar o <xref:System.Windows.Data.ObjectDataProvider> classe, como no exemplo a seguir:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Definir a associação da mesma forma, como a linha realçada que contém o `<TextBlock>` mostra do elemento.  
  
 Nesse exemplo específico, o resultado é o mesmo: você tem um <xref:System.Windows.Controls.TextBlock> com o conteúdo de texto `Joe`. No entanto, o <xref:System.Windows.Data.ObjectDataProvider> classe fornece funcionalidades como a capacidade de associar ao resultado de um método. Você pode optar por usar o <xref:System.Windows.Data.ObjectDataProvider> classe se você precisar da funcionalidade que ele fornece.  
  
 No entanto, se estiver associando a um objeto que já foi criado, será necessário definir o `DataContext` no código, como no exemplo a seguir.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Para acessar [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados para associação usando o <xref:System.Windows.Data.XmlDataProvider> classe, consulte [associar a dados XML usando um XMLDataProvider e consultas XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Para acessar [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados para associação usando o <xref:System.Windows.Data.ObjectDataProvider> classe, consulte [associar a XDocument, XElement ou LINQ para resultados de consulta XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Para obter informações sobre várias maneiras que você pode especificar os dados que você está associando a, consulte [especificar a origem da associação](how-to-specify-the-binding-source.md). Para obter informações sobre a quais tipos de dados é possível associar ou como implementar seus próprios objetos [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] para associação, consulte [Visão geral de fontes de associação](binding-sources-overview.md).  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Tópicos de instruções](data-binding-how-to-topics.md)
