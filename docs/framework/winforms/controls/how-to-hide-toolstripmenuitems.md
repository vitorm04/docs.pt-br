---
title: Como ocultar ToolStripMenuItems
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding
- MenuStrip control [Windows Forms], hiding menu items
- menus [Windows Forms], hiding menu items
- menu items [Windows Forms], hiding
- hiding menu items
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
ms.openlocfilehash: 73f67bbe6b2d51a59b6f72ab5faf21db9d6db12d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hide-toolstripmenuitems"></a>Como ocultar ToolStripMenuItems
Ocultando itens de menu é uma maneira de controlar a interface do usuário do seu aplicativo e restringir os comandos do usuário. Geralmente, é recomendável ocultar um menu inteiro quando todos os itens de menu estão indisponíveis. Isso apresenta menos distrações para o usuário. Além disso, pode ser útil ocultar e desabilitar o menu ou item de menu, visto que apenas ocultar não impede que o usuário acesse um comando de menu usando uma tecla de atalho.  
  
### <a name="to-hide-any-menu-item-programmatically"></a>Para ocultar qualquer item de menu programaticamente  
  
-   Dentro do método onde você define as propriedades do item de menu, adicione código para definir o <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade `false`.  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 [Visão geral do controle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [Como desabilitar ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)
