---
title: Como alinhar e alongar um controle em um controle TableLayoutPanel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 043adb68b88ab031cea3de1206d1f2c4252b75d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a>Como alinhar e alongar um controle em um controle TableLayoutPanel
Você pode alinhar e Alongar controles em um <xref:System.Windows.Forms.TableLayoutPanel> com o <xref:System.Windows.Forms.Control.Anchor%2A> e <xref:System.Windows.Forms.Control.Dock%2A> propriedades.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-align-and-stretch-a-control"></a>Para alinhar e alongar um controle  
  
1.  Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.  
  
2.  Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** na célula superior esquerda do <xref:System.Windows.Forms.TableLayoutPanel> controle. O <xref:System.Windows.Forms.Button> controle é centralizado na célula.  
  
3.  Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Left,Right`. O <xref:System.Windows.Forms.Button> controlar expande para corresponder à largura da célula.  
  
4.  Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Top,Bottom`. O <xref:System.Windows.Forms.Button> controlar expande para corresponder a altura da célula.  
  
5.  Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>. O <xref:System.Windows.Forms.Button> controle se expande para preencher a célula.  
  
6.  Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.None>. O <xref:System.Windows.Forms.Button> controle retorna ao tamanho original e move para o canto superior esquerdo da célula. O **Windows Forms Designer** definiu o <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Top, Left`.  
  
7.  Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Bottom,Right`. O <xref:System.Windows.Forms.Button> move o controle para o canto inferior direito da célula.  
  
8.  Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade <xref:System.Windows.Forms.AnchorStyles.None>. O <xref:System.Windows.Forms.Button> move o controle para o centro da célula.  
  
## <a name="see-also"></a>Consulte também  
 [Controle TableLayoutPanel](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
