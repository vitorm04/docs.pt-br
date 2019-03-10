---
title: 'Como: Configurar a mesclagem de Menu automática para aplicativos MDI'
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
ms.openlocfilehash: 152db39e7c947d5a49eaed81b00d13c02aa8014c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719722"
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a>Como: Configurar a mesclagem de Menu automática para aplicativos MDI
O procedimento a seguir fornece as etapas básicas para configurar a mesclagem automática em um aplicativo de interface de documentos múltiplos (MDI) com <xref:System.Windows.Forms.MenuStrip>.  
  
### <a name="to-set-up-automatic-menu-merging"></a>Para configurar a mesclagem de menu automática  
  
1.  Criar o formulário pai MDI, definindo sua <xref:System.Windows.Forms.Form.IsMdiContainer%2A> propriedade para `true`.  
  
2.  Adicionar um <xref:System.Windows.Forms.MenuStrip> para o pai MDI, configurando seus <xref:System.Windows.Forms.Form.MainMenuStrip%2A> propriedade com a <xref:System.Windows.Forms.MenuStrip>.  
  
3.  Crie um formulário MDI filho e defina seu <xref:System.Windows.Forms.Form.MdiParent%2A> propriedade para o nome do formulário pai.  
  
4.  Adicionar um <xref:System.Windows.Forms.MenuStrip> ao formulário filho MDI.  
  
5.  No formulário filho, defina as <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade do <xref:System.Windows.Forms.MenuStrip> para `false`.  
  
6.  Adicionar itens de menu para o formulário de filho <xref:System.Windows.Forms.MenuStrip> que você deseja mesclar com o formulário de pai <xref:System.Windows.Forms.MenuStrip> quando o formulário filho é ativado.  
  
7.  Use o <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> itens de propriedade no menu do formulário filho <xref:System.Windows.Forms.MenuStrip> para controlar como mesclar o formulário pai.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Visão geral do controle MenuStrip](menustrip-control-overview-windows-forms.md)
