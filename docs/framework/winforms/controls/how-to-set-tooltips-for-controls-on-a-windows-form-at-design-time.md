---
title: Como definir ToolTips para controles em um Windows Form no momento do design
description: Saiba como definir dicas de ferramenta para controles programaticamente ou na Designer de Formulários do Windows no Visual Studio.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 15134b38d11de30d0e6a2f998f6ea266affc40d7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325973"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>Como definir dicas de ferramentas para controles em um formulário do Windows em tempo de design

Você pode definir uma <xref:System.Windows.Forms.ToolTip> cadeia de caracteres no código ou na Designer de formulários do Windows no Visual Studio. Para obter mais informações sobre o <xref:System.Windows.Forms.ToolTip> componente, consulte [visão geral do componente de dica de ferramenta](tooltip-component-overview-windows-forms.md).

## <a name="set-a-tooltip-programmatically"></a>Definir uma dica de ferramenta programaticamente

1. Adicione o controle que exibirá a dica de ferramenta.

2. Use o <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> método do <xref:System.Windows.Forms.ToolTip> componente.

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

1. No Visual Studio, adicione um <xref:System.Windows.Forms.ToolTip> componente ao formulário.

2. Selecione o controle que exibirá a dica de ferramenta ou adicione-a ao formulário.

3. Na janela **Propriedades** , defina a **dica de ferramenta no valor ToolTip1** como uma cadeia de texto apropriada.

### <a name="to-remove-a-tooltip-programmatically"></a>Para remover uma dica de ferramenta programaticamente

1. Use o <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> método do <xref:System.Windows.Forms.ToolTip> componente.

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

2. Na janela **Propriedades** , exclua o texto na **dica de ferramenta em ToolTip1**.

## <a name="see-also"></a>Veja também

- [Visão geral do componente ToolTip](tooltip-component-overview-windows-forms.md)
- [Como alterar o atraso do componente ToolTip dos Windows Forms](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [Componente ToolTip](tooltip-component-windows-forms.md)
