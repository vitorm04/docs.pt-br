---
title: 'Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock
helpviewer_keywords:
- layout [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
- TableLayoutPanel control [Windows Forms], child controls
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
ms.openlocfilehash: 0e565b56c31d0776f6e89bbbe0b0681ae184758e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922817"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a>Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel
O <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.Control.Dock%2A> controle<xref:System.Windows.Forms.Control.Anchor%2A> oferece suporte às propriedades e em seus controles filho.  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a>Alinhar um controle filho a uma célula TableLayoutPanel  
  
1. Crie um <xref:System.Windows.Forms.TableLayoutPanel> controle no formulário.  
  
2. Defina o valor <xref:System.Windows.Forms.TableLayoutPanel> das propriedades <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> e <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> do controle como **1**.  
  
3. Crie um <xref:System.Windows.Forms.Button> controle <xref:System.Windows.Forms.TableLayoutPanel> no controle. O <xref:System.Windows.Forms.Button> ocupa o canto superior esquerdo da célula.  
  
4. Altere o valor da propriedade <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> para `Left`. O <xref:System.Windows.Forms.Button> controle é movido para alinhar com a borda esquerda da célula.  
  
    > [!NOTE]
    > Esse comportamento difere do comportamento de outras caixas de controles. Em outros controles de contêiner, o controle filho não se move quando <xref:System.Windows.Forms.Control.Anchor%2A> a propriedade é definida, e a distância entre o controle ancorado e o limite do contêiner pai é fixa no momento <xref:System.Windows.Forms.Control.Anchor%2A> em que a propriedade é definida.  
  
5. Altere o valor da propriedade <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> para `Top, Left`. O <xref:System.Windows.Forms.Button> controle é movido para ocupar o canto superior esquerdo da célula.  
  
6. Repita a etapa 5 com um valor `Top, Right` de para mover <xref:System.Windows.Forms.Button> o controle para o canto superior direito da célula. Repita com valores de `Bottom, Left` e `Bottom, Right`.  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a>Alongar um controle filho em uma célula TableLayoutPanel  
  
1. Altere o valor da propriedade <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> para `Left, Right`. O <xref:System.Windows.Forms.Button> controle é redimensionado para alongar pela célula.  
  
    > [!NOTE]
    > Esse comportamento difere do comportamento de outras caixas de controles. Em outros controles de contêiner, o controle filho não é redimensionado quando <xref:System.Windows.Forms.Control.Anchor%2A> a propriedade é definida `Left, Right` como `Top, Bottom`ou.  
  
2. Altere o valor da propriedade <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> para `Top, Bottom`. O <xref:System.Windows.Forms.Button> controle é redimensionado para alongar da parte superior para a parte inferior da célula.  
  
3. Altere o valor da propriedade <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> para `Top, Bottom, Left, Right`. O <xref:System.Windows.Forms.Button> controle é redimensionado para preencher a célula.  
  
4. Altere o valor da propriedade <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> para `None`. O <xref:System.Windows.Forms.Button> controle é redimensionado e centralizado na célula.  
  
5. Altere o valor da propriedade <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Dock%2A> para <xref:System.Windows.Forms.DockStyle.Left>. O <xref:System.Windows.Forms.Button> controle é movido para alinhar com a borda esquerda da célula. O <xref:System.Windows.Forms.Button> controle retém sua largura, mas sua altura é redimensionada para preencher a célula verticalmente.  
  
    > [!NOTE]
    > Esse é o mesmo comportamento que ocorre em outras caixas de controle.  
  
6. Altere o valor da propriedade <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Dock%2A> para <xref:System.Windows.Forms.DockStyle.Fill>. O <xref:System.Windows.Forms.Button> controle é redimensionado para preencher a célula.  
  
## <a name="example"></a>Exemplo  
 A ilustração a seguir mostra cinco botões ancorados em <xref:System.Windows.Forms.TableLayoutPanel> cinco células separadas.  
  
 ![Ancoragem TableLayoutPanel](./media/vs-tlpanchor.gif "VS_TLPanchor")  
  
 A ilustração a seguir mostra quatro botões ancorados nos cantos de quatro <xref:System.Windows.Forms.TableLayoutPanel> células separadas.  
  
 ![Ancoragem TableLayoutPanel](./media/vs-tlpanchor2.gif "VS_TLPanchor2")  
  
 A ilustração a seguir mostra três botões esticados pela ancoragem em três <xref:System.Windows.Forms.TableLayoutPanel> células separadas.  
  
 ![Ancoragem TableLayoutPanel](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")  
  
 O exemplo de código a seguir demonstra todas as <xref:System.Windows.Forms.Control.Anchor%2A> combinações de valores de <xref:System.Windows.Forms.Button> propriedade para um <xref:System.Windows.Forms.TableLayoutPanel> controle em um controle.  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.TableLayoutPanel>
- [Controle TableLayoutPanel](tablelayoutpanel-control-windows-forms.md)
