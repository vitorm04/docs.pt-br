---
title: Como associar a uma enumeração
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 93f33e497fd7acb81c55f86bf38737d4e7d79bf2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454446"
---
# <a name="how-to-bind-to-an-enumeration"></a>Como associar a uma enumeração
Este exemplo mostra como associar a uma enumeração ligando-se ao método GetValues da enumeração.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o <xref:System.Windows.Controls.ListBox> exibe a lista de valores de enumeração de <xref:System.Windows.HorizontalAlignment> por meio da vinculação de dados. O <xref:System.Windows.Controls.ListBox> e o <xref:System.Windows.Controls.Button> são associados, de modo que você pode alterar o valor da propriedade <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> da <xref:System.Windows.Controls.Button> selecionando um valor na <xref:System.Windows.Controls.ListBox>.  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>Consulte também

- [Associar a um método](how-to-bind-to-a-method.md)
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
