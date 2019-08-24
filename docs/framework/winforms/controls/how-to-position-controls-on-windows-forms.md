---
title: 'Como: Posicionar controles nos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Location
- Location.Y
- Location.X
helpviewer_keywords:
- controls [Windows Forms]
- controls [Windows Forms], moving
- snaplines
- controls [Windows Forms], positioning
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1cc2cb4c749b7290a6edf914a8e6a697006ef43c
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987079"
---
# <a name="how-to-position-controls-on-windows-forms"></a>Como: Posicionar controles em Windows Forms

Para posicionar controles, use o designer de formulários do Windows no Visual Studio ou especifique <xref:System.Windows.Forms.Control.Location%2A> a propriedade.

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Posicionar um controle na superfície de design do Designer de Formulários do Windows

No Visual Studio, arraste o controle para o local apropriado com o mouse.

> [!NOTE]
> Selecione o controle e mova-o com as teclas de direção para posicioná-lo com mais precisão. Além disso, as *guias de alinhamento* ajudam a posicionar os controles com precisão em seu formulário. Para obter mais informações, confira [Passo a passo: Organizando controles em Windows Forms usando Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

## <a name="position-a-control-using-the-properties-window"></a>Posicionar um controle usando o janela Propriedades

1. No Visual Studio, selecione o controle que você deseja posicionar.

2. Na janela **Propriedades** , insira valores para a <xref:System.Windows.Forms.Control.Location%2A> Propriedade, separados por uma vírgula, para posicionar o controle dentro de seu contêiner.

   O primeiro número (X) é a distância entre a borda esquerda do contêiner; o segundo número (Y) é a distância entre a borda superior da área do recipiente, medida em pixels.

   > [!NOTE]
   > Você pode expandir a <xref:System.Windows.Forms.Control.Location%2A> propriedade para digitar os valores **X** e **Y** individualmente.

## <a name="position-a-control-programmatically"></a>Posicionar um controle programaticamente

1. Defina a <xref:System.Windows.Forms.Control.Location%2A> Propriedade do controle como um <xref:System.Drawing.Point>.

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. Altere a coordenada X do local do controle usando o <xref:System.Windows.Forms.Control.Left%2A> subpropriedade.

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a>Incrementar o local de um controle programaticamente

<xref:System.Windows.Forms.Control.Left%2A> Defina subpropriedade para incrementar a coordenada X do controle.

```vb
Button1.Left += 200
```

```csharp
button1.Left += 200;
```

```cpp
button1->Left += 200;
```

> [!NOTE]
> Use a <xref:System.Windows.Forms.Control.Location%2A> propriedade para definir as posições X e Y de um controle simultaneamente. Para definir uma posição individualmente, use o <xref:System.Windows.Forms.Control.Left%2A> (**X**) ou <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subpropriedade do controle. Não tente definir implicitamente as coordenadas X e Y da <xref:System.Drawing.Point> estrutura que representa o local do botão, pois essa estrutura contém uma cópia das coordenadas do botão.

## <a name="see-also"></a>Consulte também

- [Controles dos Windows Forms](index.md)
- [Passo a passo: Organizando controles em Windows Forms usando Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Passo a passo: Organizando controles em Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Passo a passo: Organizando controles em Windows Forms usando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)
- [Controles dos Windows Forms por função](windows-forms-controls-by-function.md)
- [Como: Definir o local da tela de Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))
