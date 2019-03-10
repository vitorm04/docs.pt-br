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
ms.openlocfilehash: 127ab849fffb586261f1ac25f74f540c0f46d295
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714795"
---
# <a name="tablelayoutpanel-control-overview"></a>Visão geral do controle TableLayoutPanel
O <xref:System.Windows.Forms.TableLayoutPanel> controle organiza seu conteúdo em uma grade. Como o layout é executado tanto em tempo de design quanto em tempo de execução, ele pode ser alterado dinamicamente à medida que o ambiente do aplicativo muda. Assim, os controles no painel têm a capacidade de redimensionar proporcionalmente, portanto ele pode responder a alterações como o redimensionamento do controle pai ou à alteração de comprimento do texto devido à localização.  
  
 Qualquer controle dos Windows Forms pode ser um filho de <xref:System.Windows.Forms.TableLayoutPanel> controle, incluindo outra instâncias de <xref:System.Windows.Forms.TableLayoutPanel>. Isso permite criar layouts sofisticados que se adaptam às alterações no tempo de execução.  
  
 O <xref:System.Windows.Forms.TableLayoutPanel> controle pode ser expandido para acomodar novos controles quando eles forem adicionados, dependendo do valor da <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, e <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> propriedades. Configuração tanto a <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> ou <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> propriedade para um valor de 0 especifica que o <xref:System.Windows.Forms.TableLayoutPanel> será desassociado na direção correspondente.  
  
 Você também pode controlar a direção de expansão (horizontal ou vertical) após o <xref:System.Windows.Forms.TableLayoutPanel> controle está repleto de controles filho. Por padrão, o <xref:System.Windows.Forms.TableLayoutPanel> controle se expande para baixo adicionando linhas.  
  
 Se você quiser linhas e colunas que se comportam de forma diferente do comportamento padrão, você pode controlar as propriedades de linhas e colunas usando o <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> e <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> propriedades. É possível definir as propriedades de linhas ou colunas individualmente.  
  
 O <xref:System.Windows.Forms.TableLayoutPanel> controle adiciona as seguintes propriedades para seus controles filho: `Cell`, `Column`, `Row`, `ColumnSpan`, e `RowSpan`.  
  
 Você pode mesclar células na <xref:System.Windows.Forms.TableLayoutPanel> controle definindo o `ColumnSpan` ou `RowSpan` propriedades em um controle filho.  
  
1.  [Como: Alinhar e Alongar um controle em um controle TableLayoutPanel](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [Como: Abranger linhas e colunas em um controle TableLayoutPanel](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3.  [Como: Editar colunas e linhas em um controle TableLayoutPanel](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4.  [Passo a passo: Organizando controles nos Windows Forms utilizando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutSettings>
- [Como: Projetar um Layout de formulários do Windows que responde bem à localização](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [Como: Criar um formulário do Windows redimensionável para entrada de dados](how-to-create-a-resizable-windows-form-for-data-entry.md)
- [Práticas recomendadas para o controle TableLayoutPanel](best-practices-for-the-tablelayoutpanel-control.md)
