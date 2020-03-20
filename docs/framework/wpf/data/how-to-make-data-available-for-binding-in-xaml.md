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
ms.openlocfilehash: 91e89dbf36024c31f4afcd9b6d956944baf13576
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174180"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Como disponibilizar dados para associação em XAML
Este tópico discute várias maneiras de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]disponibilizar dados para vinculação, dependendo das necessidades de sua aplicação.  
  
## <a name="example"></a>Exemplo  
 Se você tem um objeto de tempo de execução de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]linguagem comum (CLR) que você gostaria de vincular a `x:Key`partir de , uma maneira que você pode tornar o objeto disponível para vinculação é defini-lo como um recurso e dar-lhe um . No exemplo a seguir, temos um objeto `Person` com uma propriedade de cadeia de caracteres denominada `PersonName`. O `Person` objeto (na linha mostrada `<src>` destacada que contém o `SDKSample`elemento) é definido no namespace chamado .  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Em seguida, <xref:System.Windows.Controls.TextBlock> você pode vincular [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]o controle ao objeto, como mostra a linha destacada que contém o `<TextBlock>` elemento.
  
 Alternativamente, você pode <xref:System.Windows.Data.ObjectDataProvider> usar a classe, como no exemplo a seguir:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Você define a vinculação da mesma forma, `<TextBlock>` como a linha destacada que contém o elemento mostra.  
  
 Neste exemplo em particular, o resultado é <xref:System.Windows.Controls.TextBlock> o mesmo: você tem um com o conteúdo `Joe`do texto . No entanto, a <xref:System.Windows.Data.ObjectDataProvider> classe fornece funcionalidades como a capacidade de se vincular ao resultado de um método. Você pode optar <xref:System.Windows.Data.ObjectDataProvider> por usar a classe se precisar da funcionalidade que ela fornece.  
  
 No entanto, se estiver associando a um objeto que já foi criado, será necessário definir o `DataContext` no código, como no exemplo a seguir.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Para acessar os dados XML para vincular usando a classe, consulte <xref:System.Windows.Data.XmlDataProvider> [Vincular-se aos dados XML usando um XMLDataProvider e consultas XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Para acessar os dados XML para vincular usando a <xref:System.Windows.Data.ObjectDataProvider> classe, consulte [Vincular-se a XDocument, XElement ou LINQ para obter resultados de consulta XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Para obter informações sobre muitas maneiras que você pode especificar os dados aos quais você está vinculando, consulte [Especificar a Fonte de Vinculação](how-to-specify-the-binding-source.md). Para obter informações sobre quais tipos de dados você pode vincular ou como implementar seus próprios objetos CLR (Common Language Runtime, tempo de execução de idiomas comuns) para vinculação, consulte [Visão geral de fontes de vinculação](binding-sources-overview.md).  
  
## <a name="see-also"></a>Confira também

- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Tópicos de como fazer](data-binding-how-to-topics.md)
