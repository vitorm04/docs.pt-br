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
ms.openlocfilehash: a215b2b4e05bab5c81d2779d4b67d5b9d57b6ba5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039693"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>Como: Abranger linhas e colunas em um controle TableLayoutPanel
Controles em um <xref:System.Windows.Forms.TableLayoutPanel> controle podem abranger linhas e colunas adjacentes.

## <a name="to-span-columns-and-rows"></a>Para abranger colunas e linhas

1. Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controle da **caixa de ferramentas** para seu formulário.

2. Arraste um <xref:System.Windows.Forms.Button> controle da **caixa de ferramentas** para a célula superior <xref:System.Windows.Forms.TableLayoutPanel> esquerda do controle.

3. Defina a <xref:System.Windows.Forms.Button> propriedade **ColumnSpan** do controle como **2**. Observe que o <xref:System.Windows.Forms.Button> controle abrange a primeira e a segunda colunas.

4. Defina a <xref:System.Windows.Forms.Button> propriedade **RowSpan** do controle como **2**. Observe que o <xref:System.Windows.Forms.Button> controle abrange a primeira e a segunda linhas.

5. Defina a <xref:System.Windows.Forms.Button> propriedade **ColumnSpan** do controle como **1**. Observe que o <xref:System.Windows.Forms.Button> controle é movido para a primeira coluna e abrange a primeira e a segunda linhas.

## <a name="see-also"></a>Consulte também

- [Controle TableLayoutPanel](tablelayoutpanel-control-windows-forms.md)
