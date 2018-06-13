---
title: Visão geral do componente ToolTip (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
ms.openlocfilehash: e31bb1169eeedd85a92e3bf96318623696020f9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535532"
---
# <a name="tooltip-component-overview-windows-forms"></a>Visão geral do componente ToolTip (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ToolTip> componente exibe texto quando o usuário aponta para controles. Uma dica de ferramenta pode ser associada a qualquer controle. Um exemplo de uso desse componente: para economizar espaço em um formulário, você pode exibir um pequeno ícone em um botão e usar uma dica de ferramenta para explicar a função do botão.  
  
## <a name="working-with-the-tooltip-component"></a>Trabalhando com o componente ToolTip  
 Um <xref:System.Windows.Forms.ToolTip> componente fornece um `ToolTip` propriedade para vários controles em um formulário do Windows ou outro contêiner. Por exemplo, se você colocar um <xref:System.Windows.Forms.ToolTip> componente em um formulário, você pode exibir "Digite seu nome aqui" para um <xref:System.Windows.Forms.TextBox> controlar e "Clique aqui para salvar as alterações" para um <xref:System.Windows.Forms.Button> controle.  
  
 Os principais métodos do <xref:System.Windows.Forms.ToolTip> componente são <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> e <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>. Você pode usar o <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> método para definir as dicas de ferramenta exibidas para controles. Para obter mais informações, consulte [Como definir ToolTips para controles em um Windows Form no tempo de design](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md). As propriedades de chave são <xref:System.Windows.Forms.ToolTip.Active%2A>, que deve ser definido como `true` para a dica de ferramenta, e <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, que define o período de tempo que a cadeia de caracteres de dica de ferramenta é exibida, quanto tempo o usuário deve apontar para o controle para a dica de ferramenta e como tempo leva para windows subsequente de dica de ferramenta apareça. Para obter mais informações, consulte [Como alterar o atraso do componente ToolTip dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolTip>  
 [Como definir ToolTips para controles em um Windows Form no tempo de design](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [Como alterar o atraso do componente ToolTip dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
