---
title: 'Como: Definir ToolTips para controles em um Windows Form no momento do design'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 0d6725fc1a00826870e6400bffce63a1788e802c
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211695"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>Como: Definir ToolTips para controles em um Windows Form no tempo de design

Você pode definir um <xref:System.Windows.Forms.ToolTip> cadeia de caracteres no código ou no Designer de formulários do Windows no Visual Studio. Para obter mais informações sobre o <xref:System.Windows.Forms.ToolTip> componente, consulte [visão geral do componente ToolTip](tooltip-component-overview-windows-forms.md).

## <a name="set-a-tooltip-programmatically"></a>Definir uma dica de ferramenta de forma programática

1. Adicione o controle que exibirá a dica de ferramenta.

2. Use o <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> método da <xref:System.Windows.Forms.ToolTip> componente.

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

## <a name="set-a-tooltip-in-the-designer"></a>Definir uma dica de ferramenta no designer

1. No Visual Studio, adicione um <xref:System.Windows.Forms.ToolTip> componente para o formulário.

2. Selecione o controle que será exibir a dica de ferramenta ou adicioná-lo ao formulário.

3. No **propriedades** janela, defina as **dica de ferramenta no ToolTip1** valor a ser uma cadeia de caracteres apropriada de texto.

### <a name="to-remove-a-tooltip-programmatically"></a>Para remover uma dica de ferramenta de forma programática

1. Use o <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> método da <xref:System.Windows.Forms.ToolTip> componente.

    ```vb
    ' In this example, Button1 is the control displaying the ToolTip.
    ToolTip1.SetToolTip(Button1, Nothing)
    ```

    ```csharp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1.SetToolTip(button1, null);
    ```

    ```cpp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1->SetToolTip(button1, NULL);
    ```

## <a name="remove-a-tooltip-in-the-designer"></a>Remover uma dica de ferramenta no designer

1. No Visual Studio, selecione o controle que está exibindo a dica de ferramenta.

2. No **propriedades** janela, exclua o texto na **dica de ferramenta no ToolTip1**.

## <a name="see-also"></a>Consulte também

- [Visão geral do componente ToolTip](tooltip-component-overview-windows-forms.md)
- [Como: Alterar o atraso do componente ToolTip dos Windows Forms](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [Componente ToolTip](tooltip-component-windows-forms.md)
