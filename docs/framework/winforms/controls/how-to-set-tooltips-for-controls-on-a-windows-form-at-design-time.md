---
title: Como definir ToolTips para controles em um Windows Form no momento do design
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 7f698a517fbf72ceafde4a117b4d92dd9d352834
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44360241"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>Como definir ToolTips para controles em um Windows Form no momento do design
Você pode definir um <xref:System.Windows.Forms.ToolTip> cadeia de caracteres no código ou no Designer de formulários do Windows. Para obter mais informações sobre o <xref:System.Windows.Forms.ToolTip> componente, consulte [visão geral do componente ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-a-tooltip-programmatically"></a>Para definir uma dica de ferramenta de forma programática  
  
1.  Adicione o controle que exibirá a dica de ferramenta.  
  
2.  Use o <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> método da <xref:System.Windows.Forms.ToolTip> componente.  
  
    ```vb  
    ' In this example, Button1 is the control to display the ToolTip.  
    ToolTip1.SetToolTip(Button1, "Save changes")  
    ```  
  
    ```csharp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1.SetToolTip(button1, "Save changes");  
    ```  
  
    ```cpp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1->SetToolTip(button1, "Save changes");  
    ```  
  
### <a name="to-set-a-tooltip-in-the-designer"></a>Para definir uma dica de ferramenta no designer  
  
1.  Adicionar um <xref:System.Windows.Forms.ToolTip> componente para o formulário.  
  
2.  Selecione o controle que será exibir a dica de ferramenta ou adicioná-lo ao formulário.  
  
3.  No **propriedades** janela, defina as **dica de ferramenta no ToolTip1** valor a ser uma cadeia de caracteres apropriada de texto.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do componente ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [Como alterar o atraso do componente ToolTip dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
 [Componente ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
