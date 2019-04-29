---
title: 'Como: Produzir um valor com base em uma lista de itens associados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
ms.openlocfilehash: c2ec5ff26c89649294df266e790445e5aa5d08ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931373"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a>Como: Produzir um valor com base em uma lista de itens associados
<xref:System.Windows.Data.MultiBinding> permite que você associar uma propriedade de destino da associação a uma lista de propriedades da fonte e, em seguida, aplicar a lógica para produzir um valor com as entradas disponíveis. Este exemplo demonstra como usar <xref:System.Windows.Data.MultiBinding>.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, `NameListData` refere-se a uma coleção de objetos de `PersonName`, que são objetos que contêm duas propriedades, `firstName` e `lastName`. O exemplo a seguir produz um <xref:System.Windows.Controls.TextBlock> que mostra os nomes e sobrenomes de uma pessoa com o sobrenome em primeiro lugar.  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 Para entender como o formato de sobrenome primeiro é produzido, vamos dar uma olhada na implementação do `NameConverter`:  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` implementa a interface <xref:System.Windows.Data.IMultiValueConverter>. O `NameConverter` usa os valores das associações individuais e os armazena na matriz de objetos de valores. A ordem na qual o <xref:System.Windows.Data.Binding> elementos aparecem sob o <xref:System.Windows.Data.MultiBinding> elemento é a ordem na qual esses valores são armazenados na matriz. O valor da <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> atributo é referenciado pelo argumento do parâmetro a <xref:System.Windows.Data.MultiBinding.Converter%2A> método, que executa uma troca no parâmetro para determinar como formatar o nome.  
  
## <a name="see-also"></a>Consulte também

- [Converter dados associados](how-to-convert-bound-data.md)
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Tópicos de instruções](data-binding-how-to-topics.md)
