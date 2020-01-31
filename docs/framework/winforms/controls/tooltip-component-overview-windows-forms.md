---
title: Visão geral do componente ToolTip
ms.date: 03/30/2017
f1_keywords:
- ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
ms.openlocfilehash: 731f7ad0ce6670000d8c3d3e901e1506f7ef470a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741910"
---
# <a name="tooltip-component-overview-windows-forms"></a>Visão geral do componente ToolTip (Windows Forms)
O componente Windows Forms <xref:System.Windows.Forms.ToolTip> exibe texto quando o usuário aponta para os controles. Uma dica de ferramenta pode ser associada a qualquer controle. Um exemplo de uso desse componente: para economizar espaço em um formulário, você pode exibir um pequeno ícone em um botão e usar uma dica de ferramenta para explicar a função do botão.  
  
## <a name="working-with-the-tooltip-component"></a>Trabalhando com o componente ToolTip  
 Um componente <xref:System.Windows.Forms.ToolTip> fornece uma propriedade `ToolTip` para vários controles em um formulário do Windows ou outro contêiner. Por exemplo, se você coloca um componente <xref:System.Windows.Forms.ToolTip> em um formulário, você pode exibir "Digite seu nome aqui" para um controle de <xref:System.Windows.Forms.TextBox> e "clique aqui para salvar as alterações" para um controle de <xref:System.Windows.Forms.Button>.  
  
 Os principais métodos do componente <xref:System.Windows.Forms.ToolTip> são <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> e <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>. Você pode usar o método <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> para definir as dicas de ferramenta exibidas para controles. Para obter mais informações, consulte [Como definir ToolTips para controles em um Windows Form no tempo de design](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md). As propriedades de chave são <xref:System.Windows.Forms.ToolTip.Active%2A>, que devem ser definidas como `true` para que a dica de ferramenta apareça e <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, que define o período de tempo que a cadeia de caracteres de dica de ferramenta é mostrada, por quanto tempo o usuário deve apontar para o controle para que a dica de ferramenta apareça e quanto tempo leva para que janelas de dica de ferramenta subsequentes apareçam. Para obter mais informações, consulte [Como alterar o atraso do componente ToolTip dos Windows Forms](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.ToolTip>
- [Como definir ToolTips para controles em um Windows Form no tempo de design](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [Como alterar o atraso do componente ToolTip dos Windows Forms](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
