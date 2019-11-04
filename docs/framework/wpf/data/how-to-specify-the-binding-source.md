---
title: Como especificar a origem da associação
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 4fde66b22bac6b4a2cfeb4eceb50027daadee387
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454358"
---
# <a name="how-to-specify-the-binding-source"></a>Como especificar a origem da associação
Na associação de dados, o objeto da origem de associação refere-se àquele cujos dados você deseja obter. Este tópico descreve as diferentes maneiras de especificar a origem da associação.  
  
## <a name="example"></a>Exemplo  
 Se você estiver associando várias propriedades a uma fonte comum, será recomendável usar a propriedade `DataContext`, que fornece uma maneira conveniente para estabelecer um escopo dentro do qual todas as propriedades associadas a dados herdarão uma fonte comum.  
  
 No exemplo a seguir, o contexto de dados é estabelecido no elemento raiz do aplicativo. Isso permite que todos os elementos filho herdem esse contexto de dados. Os dados para a associação provêm de uma classe personalizada de dados, `NetIncome`, referenciada diretamente por meio de um mapeamento e com a chave de recurso de `incomeDataSource` concedida.  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 O exemplo a seguir mostra a definição da classe `NetIncome`.  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
> O exemplo acima instancia o objeto na marcação e o utiliza como um recurso. Se você deseja associar a um objeto já instanciado no código, é necessário definir a propriedade `DataContext` com programação. Por exemplo, consulte [Disponibilizar dados para associação em XAML](how-to-make-data-available-for-binding-in-xaml.md).  
  
 Como alternativa, se quiser especificar a fonte em suas associações individuais explicitamente, você terá as opções a seguir. Eles têm precedência sobre o contexto de dados herdado.  
  
|propriedade|Descrição|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|Você pode usar essa propriedade para definir a fonte para uma instância de um objeto. Se você não precisar da funcionalidade de estabelecer um escopo no qual várias propriedades herdam o mesmo contexto de dados, você poderá usar a propriedade <xref:System.Windows.Data.Binding.Source%2A> em vez da propriedade `DataContext`. Para obter mais informações, consulte <xref:System.Windows.Data.Binding.Source%2A>.|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|Isso é útil quando você deseja especificar a fonte com relação a onde está o seu destino de associação. Alguns cenários comuns em que você pode usar essa propriedade é quando você deseja associar uma propriedade do seu elemento a outra propriedade do mesmo elemento ou caso esteja definindo uma associação em um estilo ou um modelo. Para obter mais informações, consulte <xref:System.Windows.Data.Binding.RelativeSource%2A>.|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|Especifique uma cadeia de caracteres que representa o elemento ao qual você deseja associar. Isso é útil quando você deseja associar à propriedade de outro elemento em seu aplicativo. Por exemplo, se você quiser usar uma <xref:System.Windows.Controls.Slider> para controlar a altura de outro controle em seu aplicativo ou se quiser associar a <xref:System.Windows.Controls.ContentControl.Content%2A> do seu controle à propriedade <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> do seu controle de <xref:System.Windows.Controls.ListBox>. Para obter mais informações, consulte <xref:System.Windows.Data.Binding.ElementName%2A>.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [Herança do valor da propriedade](../advanced/property-value-inheritance.md)
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Visão geral das declarações de associação](binding-declarations-overview.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
