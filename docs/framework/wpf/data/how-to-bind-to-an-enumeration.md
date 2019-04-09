---
title: 'Como: Associar a uma enumeração'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 5026261366d6abde82790f05780d8ba2c29c4a49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210016"
---
# <a name="how-to-bind-to-an-enumeration"></a>Como: Associar a uma enumeração
Este exemplo mostra como associar a uma enumeração associando ao método GetValues da enumeração.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o <xref:System.Windows.Controls.ListBox> exibe a lista de <xref:System.Windows.HorizontalAlignment> valores de enumeração por meio da vinculação de dados. O <xref:System.Windows.Controls.ListBox> e o <xref:System.Windows.Controls.Button> são vinculados, de modo que você pode alterar o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> valor da propriedade da <xref:System.Windows.Controls.Button> selecionando um valor no <xref:System.Windows.Controls.ListBox>.  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>Consulte também

- [Associar a um método](how-to-bind-to-a-method.md)
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Tópicos explicativos ](data-binding-how-to-topics.md)
