---
title: Como configurar a mesclagem de menu automática para aplicativos MDI
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
ms.openlocfilehash: e308ef8327fc439f52c4e3476a663f47fa00a379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533455"
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a>Como configurar a mesclagem de menu automática para aplicativos MDI
O procedimento a seguir fornece as etapas básicas para configurar uma mesclagem automática em um aplicativo de interface de documentos múltiplos (MDI) com <xref:System.Windows.Forms.MenuStrip>.  
  
### <a name="to-set-up-automatic-menu-merging"></a>Para configurar a mesclagem de menu automática  
  
1.  Criar o formulário pai MDI definindo seu <xref:System.Windows.Forms.Form.IsMdiContainer%2A> propriedade `true`.  
  
2.  Adicionar um <xref:System.Windows.Forms.MenuStrip> para o pai MDI, definindo seu <xref:System.Windows.Forms.Form.MainMenuStrip%2A> propriedade ao <xref:System.Windows.Forms.MenuStrip>.  
  
3.  Criar um formulário MDI filho e defina seu <xref:System.Windows.Forms.Form.MdiParent%2A> propriedade para o nome do formulário pai.  
  
4.  Adicionar um <xref:System.Windows.Forms.MenuStrip> para o formulário filho MDI.  
  
5.  No formulário filho, defina a <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade o <xref:System.Windows.Forms.MenuStrip> para `false`.  
  
6.  Adicionar itens de menu do formulário filho <xref:System.Windows.Forms.MenuStrip> que você deseja mesclar do formulário pai <xref:System.Windows.Forms.MenuStrip> quando o formulário filho é ativado.  
  
7.  Use o <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> itens de propriedade no menu do formulário filho <xref:System.Windows.Forms.MenuStrip> para controlar como mesclar o formulário pai.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Visão geral do controle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
