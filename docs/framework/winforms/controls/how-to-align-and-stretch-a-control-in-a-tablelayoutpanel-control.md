---
title: 'Como: Alinhar e alongar um controle em um controle TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
ms.openlocfilehash: fd32593bcad9e3f3ef93edee8aa2659d423f9feb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210358"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a>Como: Alinhar e alongar um controle em um controle TableLayoutPanel

Você pode alinhar e Alongar controles em uma <xref:System.Windows.Forms.TableLayoutPanel> com o <xref:System.Windows.Forms.Control.Anchor%2A> e <xref:System.Windows.Forms.Control.Dock%2A> propriedades.

## <a name="align-and-stretch-a-control"></a>Alinhar e Alongar um controle

1. No Visual Studio, arraste uma <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.

2. Arraste uma <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** a célula do canto superior esquerdo do <xref:System.Windows.Forms.TableLayoutPanel> controle. O <xref:System.Windows.Forms.Button> controle é centralizado na célula.

3. Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Left,Right`. O <xref:System.Windows.Forms.Button> controlar alonga para corresponder à largura da célula.

4. Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Top,Bottom`. O <xref:System.Windows.Forms.Button> controlar alonga para corresponder à altura da célula.

5. Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>. O <xref:System.Windows.Forms.Button> controle se expande para preencher a célula.

6. Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.None>. O <xref:System.Windows.Forms.Button> controle retorna ao seu tamanho original e o move para o canto superior esquerdo da célula. O **Designer de formulários do Windows** definiu o <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Top, Left`.

7. Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Bottom,Right`. O <xref:System.Windows.Forms.Button> controle se move para o canto inferior direito da célula.

8. Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade <xref:System.Windows.Forms.AnchorStyles.None>. O <xref:System.Windows.Forms.Button> controle se move para o centro da célula.

## <a name="see-also"></a>Consulte também

- [Controle TableLayoutPanel](tablelayoutpanel-control-windows-forms.md)
