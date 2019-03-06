---
title: 'Como: Associar a uma enumeração'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: df26d2bd08e4691837f739a4e71d3bb1a25bdd00
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377788"
---
# <a name="how-to-bind-to-an-enumeration"></a>Como: Associar a uma enumeração
Este exemplo mostra como associar a uma enumeração associando ao método GetValues da enumeração.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o <xref:System.Windows.Controls.ListBox> exibe a lista de <xref:System.Windows.HorizontalAlignment> valores de enumeração por meio da vinculação de dados. O <xref:System.Windows.Controls.ListBox> e o <xref:System.Windows.Controls.Button> são vinculados, de modo que você pode alterar o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> valor da propriedade da <xref:System.Windows.Controls.Button> selecionando um valor no <xref:System.Windows.Controls.ListBox>.  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>Consulte também
- [Associar a um método](how-to-bind-to-a-method.md)
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Tópicos de instruções](data-binding-how-to-topics.md)
