---
title: Como localizar um elemento pelo nome
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
ms.openlocfilehash: e2d176c9334c0a1d4c10819e0dc9f2c408e41d5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543570"
---
# <a name="how-to-find-an-element-by-its-name"></a>Como localizar um elemento pelo nome
Este exemplo descreve como usar o <xref:System.Windows.FrameworkElement.FindName%2A> método para encontrar um elemento por seu <xref:System.Windows.FrameworkElement.Name%2A> valor.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, o método para localizar um elemento específico por seu nome é gravada como o manipulador de eventos de um botão. `stackPanel` é o <xref:System.Windows.FrameworkElement.Name%2A> da raiz <xref:System.Windows.FrameworkElement> está sendo pesquisada, e o método exemplo então visualmente indica o elemento encontrado convertendo-o como <xref:System.Windows.Controls.TextBlock> e alterar um do <xref:System.Windows.Controls.TextBlock> visível [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] propriedades.  
  
 [!code-csharp[FEFindName#Find](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
