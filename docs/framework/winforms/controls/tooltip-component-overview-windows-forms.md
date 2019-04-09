---
title: Visão geral do componente ToolTip (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
ms.openlocfilehash: 3fbe883501d1ce36ca25ea07631f98042f451e07
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197302"
---
# <a name="tooltip-component-overview-windows-forms"></a>Visão geral do componente ToolTip (Windows Forms)
Os formulários do Windows <xref:System.Windows.Forms.ToolTip> componente exibe o texto quando o usuário aponta para controles. Uma dica de ferramenta pode ser associada a qualquer controle. Um exemplo de uso desse componente: para economizar espaço em um formulário, você pode exibir um pequeno ícone em um botão e usar uma dica de ferramenta para explicar a função do botão.  
  
## <a name="working-with-the-tooltip-component"></a>Trabalhando com o componente ToolTip  
 Um <xref:System.Windows.Forms.ToolTip> componente fornece um `ToolTip` propriedade a vários controles em um formulário do Windows ou outro contêiner. Por exemplo, se você colocar um <xref:System.Windows.Forms.ToolTip> componente em um formulário, você pode exibir "Digite seu nome aqui" para um <xref:System.Windows.Forms.TextBox> controlar e "Clique aqui para salvar alterações" para um <xref:System.Windows.Forms.Button> controle.  
  
 Os métodos da chave de <xref:System.Windows.Forms.ToolTip> componente estão <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> e <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>. Você pode usar o <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> método para definir as dicas de ferramenta exibidas para controles. Para obter mais informações, confira [Como: Definir ToolTips para controles em um Windows Form no tempo de Design](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md). As propriedades de chave são <xref:System.Windows.Forms.ToolTip.Active%2A>, que deve ser definido como `true` para a dica de ferramenta apareça, e <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, que define o período de tempo que a cadeia de caracteres de dica de ferramenta é mostrada, quanto tempo o usuário deve apontar para o controle da dica de ferramenta apareça e como quanto tempo necessário para que as janelas de dica de ferramenta subsequentes sejam exibidos. Para obter mais informações, confira [Como: Alterar o atraso do componente ToolTip dos Windows Forms](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ToolTip>
- [Como: Definir ToolTips para controles em um Windows Form no momento do design](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [Como: Alterar o atraso do componente ToolTip do Windows Forms](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
