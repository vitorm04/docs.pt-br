---
title: 'Como: Abranger linhas e colunas em um controle TableLayoutPanel'
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
ms.openlocfilehash: 2b2a46bf53dd6ec9bc93a74cca37dffaaaf79751
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193129"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>Como: Abranger linhas e colunas em um controle TableLayoutPanel
Controles em um <xref:System.Windows.Forms.TableLayoutPanel> controle pode abranger linhas e colunas adjacentes.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-span-columns-and-rows"></a>Para abranger linhas e colunas  
  
1.  Arraste uma <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.  
  
2.  Arraste uma <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** a célula do canto superior esquerdo do <xref:System.Windows.Forms.TableLayoutPanel> controle.  
  
3.  Defina as <xref:System.Windows.Forms.Button> do controle **ColumnSpan** propriedade **2**. Observe que o <xref:System.Windows.Forms.Button> controle abrange a primeira e segunda colunas.  
  
4.  Defina as <xref:System.Windows.Forms.Button> do controle **RowSpan** propriedade **2**. Observe que o <xref:System.Windows.Forms.Button> controle abrange as primeira e segunda linhas.  
  
5.  Defina as <xref:System.Windows.Forms.Button> do controle **ColumnSpan** propriedade **1**. Observe que o <xref:System.Windows.Forms.Button> controle passa para a primeira coluna e abrange as primeira e segunda linhas.  
  
## <a name="see-also"></a>Consulte também

- [Controle TableLayoutPanel](tablelayoutpanel-control-windows-forms.md)
