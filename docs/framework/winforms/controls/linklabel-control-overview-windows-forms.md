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
ms.openlocfilehash: 9837902bf56a402d623adbcf41558dcc568b7105
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745215"
---
# <a name="linklabel-control-overview-windows-forms"></a>Visão geral do controle LinkLabel (Windows Forms)
O controle de <xref:System.Windows.Forms.LinkLabel> de Windows Forms permite adicionar links de estilo da Web a aplicativos Windows Forms. Você pode usar o controle de <xref:System.Windows.Forms.LinkLabel> para tudo o que você pode usar para o controle de <xref:System.Windows.Forms.Label>; Você também pode definir parte do texto como um link para um arquivo, uma pasta ou uma página da Web.  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>O que você pode fazer com o Controle LinkLabel  
 Além de todas as propriedades, métodos e eventos do controle <xref:System.Windows.Forms.Label>, o <xref:System.Windows.Forms.LinkLabel> controle tem propriedades para hiperlinks e cores de link. A propriedade <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> define a área do texto que ativa o link. As propriedades <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>e <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> definem as cores do link. O evento <xref:System.Windows.Forms.LinkLabel.LinkClicked> determina o que acontece quando o texto do link é selecionado.  
  
 O uso mais simples do controle de <xref:System.Windows.Forms.LinkLabel> é exibir um único link usando a propriedade <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, mas você também pode exibir vários hiperlinks usando a propriedade <xref:System.Windows.Forms.LinkLabel.Links%2A>. A propriedade <xref:System.Windows.Forms.LinkLabel.Links%2A> permite que você acesse uma coleção de links. Você também pode especificar dados na propriedade <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> de cada objeto <xref:System.Windows.Forms.LinkLabel.Link> individual. O valor da propriedade <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> pode ser usado para armazenar o local de um arquivo a ser exibido ou o endereço de um site da Web.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.LinkLabel>
- [Visão geral do controle Label](label-control-overview-windows-forms.md)
- [Como vincular a um objeto ou página da Web com o controle LinkLabel dos Windows Forms](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [Como alterar a aparência do controle LinkLabel dos Windows Forms](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
