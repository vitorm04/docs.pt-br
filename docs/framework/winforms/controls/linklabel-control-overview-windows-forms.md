---
title: Visão geral do controle LinkLabel (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
ms.openlocfilehash: 40326a9055ff51efae5f4c64744d0966870c6f6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="linklabel-control-overview-windows-forms"></a>Visão geral do controle LinkLabel (Windows Forms)
Windows Forms <xref:System.Windows.Forms.LinkLabel> controle permite que você adicionar links de estilo da Web para aplicativos de formulários do Windows. Você pode usar o <xref:System.Windows.Forms.LinkLabel> controle tudo o que você pode usar o <xref:System.Windows.Forms.Label> controlar para; você também pode definir a parte do texto como um link para um arquivo, pasta ou página da Web.  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>O que você pode fazer com o Controle LinkLabel  
 Além de todos os métodos, propriedades e eventos de <xref:System.Windows.Forms.Label> controle, o <xref:System.Windows.Forms.LinkLabel> controle tem propriedades de hiperlinks e cores de link. O <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriedade define a área do texto que ativa o link. O <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, e <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> propriedades definidas as cores do link. O <xref:System.Windows.Forms.LinkLabel.LinkClicked> evento determina o que acontece quando o texto do link é selecionado.  
  
 O uso mais simples do <xref:System.Windows.Forms.LinkLabel> é de controle exibir um link único usando o <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriedade, mas você também pode exibir vários hiperlinks usando o <xref:System.Windows.Forms.LinkLabel.Links%2A> propriedade. O <xref:System.Windows.Forms.LinkLabel.Links%2A> propriedade permite que você acesse uma coleção de links. Você também pode especificar dados de <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> propriedade de cada indivíduo <xref:System.Windows.Forms.LinkLabel.Link> objeto. O valor de <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> propriedade pode ser usada para armazenar o local de um arquivo de vídeo ou o endereço de um site da Web.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.LinkLabel>  
 [Visão geral do controle Label](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [Como vincular a um objeto ou página da Web com o controle LinkLabel dos Windows Forms](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [Como alterar a aparência do controle LinkLabel dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
