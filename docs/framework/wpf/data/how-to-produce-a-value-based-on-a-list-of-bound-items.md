---
title: Como produzir um valor com base em uma lista de itens associados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
ms.openlocfilehash: da183a34eb85de54b1e3f54f8d14c09e25640165
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459700"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a>Como produzir um valor com base em uma lista de itens associados
<xref:System.Windows.Data.MultiBinding> permite associar uma propriedade de destino de associação a uma lista de propriedades de origem e, em seguida, aplicar a lógica para produzir um valor com as entradas fornecidas. Este exemplo demonstra como usar <xref:System.Windows.Data.MultiBinding>.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, `NameListData` refere-se a uma coleção de objetos de `PersonName`, que são objetos que contêm duas propriedades, `firstName` e `lastName`. O exemplo a seguir produz um <xref:System.Windows.Controls.TextBlock> que mostra o primeiro e o último nome de uma pessoa com o sobrenome primeiro.  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 Para entender como o formato de sobrenome primeiro é produzido, vamos dar uma olhada na implementação do `NameConverter`:  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` implementa a interface <xref:System.Windows.Data.IMultiValueConverter>. O `NameConverter` usa os valores das associações individuais e os armazena na matriz de objetos de valores. A ordem na qual os elementos de <xref:System.Windows.Data.Binding> aparecem sob o elemento <xref:System.Windows.Data.MultiBinding> é a ordem na qual esses valores são armazenados na matriz. O valor do atributo <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> é referenciado pelo argumento de parâmetro do método <xref:System.Windows.Data.MultiBinding.Converter%2A>, que executa uma opção no parâmetro para determinar como formatar o nome.  
  
## <a name="see-also"></a>Consulte também

- [Converter dados associados](how-to-convert-bound-data.md)
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
