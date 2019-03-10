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
ms.openlocfilehash: 81edab0d44ae0bb9dcabe77ad568f281e6f5fffb
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722341"
---
# <a name="linklabel-control-overview-windows-forms"></a>Visão geral do controle LinkLabel (Windows Forms)
Os formulários do Windows <xref:System.Windows.Forms.LinkLabel> controle permite que você adicione links no estilo Web para aplicativos do Windows Forms. Você pode usar o <xref:System.Windows.Forms.LinkLabel> controle de tudo o que você pode usar o <xref:System.Windows.Forms.Label> de controle para; você também pode definir a parte do texto como um link para um arquivo, pasta ou página da Web.  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>O que você pode fazer com o Controle LinkLabel  
 Além de todos os métodos, propriedades e eventos do <xref:System.Windows.Forms.Label> controle, o <xref:System.Windows.Forms.LinkLabel> controle tem propriedades para hiperlinks e cores de link. O <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriedade define a área do texto que ativa o link. O <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, e <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> propriedades definem as cores do link. O <xref:System.Windows.Forms.LinkLabel.LinkClicked> evento determina o que acontece quando o texto do link é selecionado.  
  
 O uso mais simples dos <xref:System.Windows.Forms.LinkLabel> controle é exibir um link único usando o <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriedade, mas você também pode exibir vários hiperlinks usando o <xref:System.Windows.Forms.LinkLabel.Links%2A> propriedade. O <xref:System.Windows.Forms.LinkLabel.Links%2A> propriedade permite que você acesse uma coleção de links. Você também pode especificar os dados na <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> propriedade de cada indivíduo <xref:System.Windows.Forms.LinkLabel.Link> objeto. O valor da <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> propriedade pode ser usada para armazenar o local de um arquivo para exibição ou o endereço de um site da Web.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.LinkLabel>
- [Visão geral do controle Label](label-control-overview-windows-forms.md)
- [Como: Vincular a um objeto ou página com o controle LinkLabel dos Windows Forms da Web](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [Como: Alterar a aparência do controle LinkLabel dos Windows Forms](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
