---
title: 'Como: Associar um ContextMenuStrip a um controle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [Windows Forms], relating
- ContextMenuStrips [Windows Forms], associating with controls
- context menus [Windows Forms], associating with controls
- ContextMenuStrips [Windows Forms], relating
ms.assetid: 6fc40a42-5d69-427f-aa30-0a146193226b
ms.openlocfilehash: 4e39769621c46ead92076489014f6e0e9dc7863d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122363"
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a>Como: Associar um ContextMenuStrip a um controle
Depois de criar os seus controles e menus de atalho, use os procedimentos a seguir para exibir um menu de atalho fornecido quando o usuário clica no controle. Esses procedimentos associar uma <xref:System.Windows.Forms.ContextMenuStrip> com um formulário do Windows e com um <xref:System.Windows.Forms.ToolStrip> controle.  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a>Para associar um ContextMenuStrip um formulário do Windows  
  
1.  Defina as <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propriedade para o nome do associado <xref:System.Windows.Forms.ContextMenuStrip>.  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a>Para associar um ContextMenuStrip um controle ToolStrip  
  
1.  Defina o controle <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propriedade para o nome do associado <xref:System.Windows.Forms.ContextMenuStrip>.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir cria um formulário do Windows e um <xref:System.Windows.Forms.ToolStrip>e a associa outro <xref:System.Windows.Forms.ContextMenuStrip> controle com cada um deles.  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>
- <xref:System.Windows.Forms.ToolStrip>
- [Como: Adicionar itens de menu a um ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md)
- [Controle ContextMenuStrip](contextmenustrip-control.md)
