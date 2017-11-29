---
title: "Como associar a uma enumeração"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31fb9adbda47514e5405d465c0b5e2493b966d8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-an-enumeration"></a>Como associar a uma enumeração
Este exemplo mostra como associar a uma enumeração associando ao método GetValues da enumeração.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o <xref:System.Windows.Controls.ListBox> exibe a lista de <xref:System.Windows.HorizontalAlignment> valores de enumeração por meio de associação de dados. O <xref:System.Windows.Controls.ListBox> e o <xref:System.Windows.Controls.Button> associados, de modo que você pode alterar o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> valor da propriedade a <xref:System.Windows.Controls.Button> selecionando um valor na <xref:System.Windows.Controls.ListBox>.  
  
 [!code-xaml[BindToEnum#BindToEnum](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>Consulte também  
 [Associar a um método](../../../../docs/framework/wpf/data/how-to-bind-to-a-method.md)  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tópicos explicativos](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
