---
title: 'Como: Criar um botão que tenha uma imagem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
ms.openlocfilehash: cfebe53047531ecddde42a3a0596dfd949629ecd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682042"
---
# <a name="how-to-create-a-button-that-has-an-image"></a>Como: Criar um botão que tenha uma imagem
Este exemplo mostra como incluir uma imagem em um <xref:System.Windows.Controls.Button>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria dois <xref:System.Windows.Controls.Button> controles. Um <xref:System.Windows.Controls.Button> contém o texto e o outro contém uma imagem. A imagem é em uma pasta chamada dados, que é uma subpasta da pasta do projeto de exemplo. Quando um usuário clica o <xref:System.Windows.Controls.Button> que tem a imagem, o plano de fundo e o texto dos outros <xref:System.Windows.Controls.Button> alterar.  
  
 Este exemplo cria <xref:System.Windows.Controls.Button> controla usando marcação, mas usa o código para gravar o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipuladores de eventos.  
  
 [!code-xaml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a>Consulte também
- [Controles](../../../../docs/framework/wpf/controls/index.md)
- [Biblioteca de controles](../../../../docs/framework/wpf/controls/control-library.md)
