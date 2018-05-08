---
title: Como abranger linhas e colunas em um controle TableLayoutPanel
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: a78286be8ef64212d945b3cb11a2963d5a1b2e79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>Como abranger linhas e colunas em um controle TableLayoutPanel
Controles em um <xref:System.Windows.Forms.TableLayoutPanel> controle pode abranger linhas e colunas adjacentes.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-span-columns-and-rows"></a>Para abranger linhas e colunas  
  
1.  Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.  
  
2.  Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** na célula superior esquerda do <xref:System.Windows.Forms.TableLayoutPanel> controle.  
  
3.  Definir o <xref:System.Windows.Forms.Button> do controle **ColumnSpan** propriedade **2**. Observe que o <xref:System.Windows.Forms.Button> controle abrange a primeira e segunda coluna.  
  
4.  Definir o <xref:System.Windows.Forms.Button> do controle **RowSpan** propriedade **2**. Observe que o <xref:System.Windows.Forms.Button> controle abrange as primeira e segunda linhas.  
  
5.  Definir o <xref:System.Windows.Forms.Button> do controle **ColumnSpan** propriedade **1**. Observe que o <xref:System.Windows.Forms.Button> controle move para a primeira coluna e abrange as primeira e segunda linhas.  
  
## <a name="see-also"></a>Consulte também  
 [Controle TableLayoutPanel](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
