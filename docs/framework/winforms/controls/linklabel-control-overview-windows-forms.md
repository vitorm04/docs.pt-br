---
title: Visão geral do controle LinkLabel
ms.date: 03/30/2017
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
ms.openlocfilehash: 3e8607644c858ae804e384c974b5e81c1786c6a1
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739513"
---
# <a name="linklabel-control-overview-windows-forms"></a>Visão geral do controle LinkLabel (Windows Forms)
O controle <xref:System.Windows.Forms.LinkLabel> do Windows Forms permite adicionar links no estilo Web aos aplicativos do Windows Forms. Você pode <xref:System.Windows.Forms.LinkLabel> usar o controle para <xref:System.Windows.Forms.Label> tudo o que você pode usar o controle para; você também pode definir parte do texto como um link para um arquivo, pasta ou página da Web.  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>O que você pode fazer com o Controle LinkLabel  
 Além de todas as propriedades, métodos <xref:System.Windows.Forms.Label> e eventos <xref:System.Windows.Forms.LinkLabel> do controle, o controle tem propriedades para hiperlinks e cores de link. A <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriedade define a área do texto que ativa o link. As <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>propriedades <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> e as propriedades definem as cores do link. O <xref:System.Windows.Forms.LinkLabel.LinkClicked> evento determina o que acontece quando o texto do link é selecionado.  
  
 O uso mais <xref:System.Windows.Forms.LinkLabel> simples do controle é exibir <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> um único link usando a propriedade, mas você também pode exibir vários hiperlinks usando a <xref:System.Windows.Forms.LinkLabel.Links%2A> propriedade. A <xref:System.Windows.Forms.LinkLabel.Links%2A> propriedade permite que você acesse uma coleção de links. Você também pode especificar dados <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> <xref:System.Windows.Forms.LinkLabel.Link> na propriedade de cada objeto individual. O valor <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> da propriedade pode ser usado para armazenar a localização de um arquivo para exibição ou o endereço de um site.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.LinkLabel>
- [Visão geral do controle de rótulo](label-control-overview-windows-forms.md)
- [Como vincular a um objeto ou página da Web com o controle LinkLabel dos Windows Forms](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [Como alterar a aparência do controle LinkLabel do Windows Forms](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
