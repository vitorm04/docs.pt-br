---
title: Visão geral do controle TableLayoutPanel
ms.date: 03/30/2017
f1_keywords:
- TableLayoutPanel
helpviewer_keywords:
- controls [Windows Forms], resizing
- resizable controls [Windows Forms]
- Windows Forms controls, proportional resizing
- Windows Forms, proportional resizing of controls
- layout [Windows Forms], TableLayoutPanel control
- TableLayoutPanel control [Windows Forms], about TableLayoutPanel control
ms.assetid: 337661c8-61cb-44ee-93e0-3662bddec327
ms.openlocfilehash: 4514901870d9073b611746070a1f53d01db95766
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="tablelayoutpanel-control-overview"></a>Visão geral do controle TableLayoutPanel
O <xref:System.Windows.Forms.TableLayoutPanel> controle organiza seu conteúdo em uma grade. Como o layout é executado tanto em tempo de design quanto em tempo de execução, ele pode ser alterado dinamicamente à medida que o ambiente do aplicativo muda. Assim, os controles no painel têm a capacidade de redimensionar proporcionalmente, portanto ele pode responder a alterações como o redimensionamento do controle pai ou à alteração de comprimento do texto devido à localização.  
  
 Qualquer controle de formulários do Windows pode ser um filho de <xref:System.Windows.Forms.TableLayoutPanel> controle, inclusive de outras instâncias de <xref:System.Windows.Forms.TableLayoutPanel>. Isso permite criar layouts sofisticados que se adaptam às alterações no tempo de execução.  
  
 O <xref:System.Windows.Forms.TableLayoutPanel> controle pode ser expandido para acomodar novos controles quando eles são adicionados, dependendo do valor da <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, e <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> propriedades. Configuração de <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> ou <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> propriedade para um valor de 0 especifica que o <xref:System.Windows.Forms.TableLayoutPanel> será desacoplado na direção correspondente.  
  
 Você também pode controlar a direção de expansão (horizontal ou vertical) após o <xref:System.Windows.Forms.TableLayoutPanel> controle está completo de controles filho. Por padrão, o <xref:System.Windows.Forms.TableLayoutPanel> controle se expande para baixo, adicionando linhas.  
  
 Se você desejar linhas e colunas que se comportam de maneira diferente do comportamento padrão, você pode controlar as propriedades de linhas e colunas usando o <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> e <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> propriedades. É possível definir as propriedades de linhas ou colunas individualmente.  
  
 O <xref:System.Windows.Forms.TableLayoutPanel> controle adiciona as seguintes propriedades para seus controles filhos: `Cell`, `Column`, `Row`, `ColumnSpan`, e `RowSpan`.  
  
 Você pode mesclar células no <xref:System.Windows.Forms.TableLayoutPanel> controle definindo o `ColumnSpan` ou `RowSpan` propriedades em um controle filho.  
  
1.  [Como alinhar e alongar um controle em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))  
  
2.  [Como abranger linhas e colunas em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))  
  
3.  [Como editar colunas e linhas em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))  
  
4.  [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 [Como criar um layout dos Windows Forms que responda bem à localização](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Como criar um Windows Form redimensionável para entrada de dados](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 [Práticas recomendadas para o controle TableLayoutPanel](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
