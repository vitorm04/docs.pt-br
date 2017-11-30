---
title: "Visão geral do controle DomainUpDown (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0692677b8ef596bb31b1869480603573a9ec98d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="domainupdown-control-overview-windows-forms"></a>Visão geral do controle DomainUpDown (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DomainUpDown> controle é essencialmente uma combinação de uma caixa de texto e um par de botões para cima ou para baixo em uma lista. O controle exibe e define uma sequências de texto em uma lista de escolhas. O usuário pode selecionar a sequência clicando nos botões para cima e para baixo para mover a lista, apertando as teclas de direção PARA BAIXO e PARA CIMA ou digitando uma cadeia de caracteres que corresponda a um item na lista. Um possível uso para este controle é selecionar itens de uma lista de nomes ordenada alfabeticamente.  
  
> [!NOTE]
>  Para classificar a lista, defina o <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> propriedade `true`.  
  
 A função deste controle é bem parecida com a da caixa de listagem ou caixa de combinação, mas ocupa muito pouco espaço.  
  
## <a name="key-properties"></a>Propriedades da chave  
 As propriedades de chave do controle são <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, e <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. O <xref:System.Windows.Forms.DomainUpDown.Items%2A> propriedade contém a lista de objetos cujos valores de texto são exibidos no controle. Se <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> é definido como `false`, o controle preenche automaticamente o texto que o usuário digita e faz a correspondência com um valor na lista. Se <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> é definido como `true`, após o último item de rolagem levará você para o primeiro item na lista e vice-versa. Os métodos de chave do controle são <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> e <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Este controle exibe somente sequências de texto. Se você quiser um controle que exibe valores numéricos, use o <xref:System.Windows.Forms.NumericUpDown> controle. Para mais informação, consulte [Visão geral do controle NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DomainUpDown>  
 [Controle DomainUpDown](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)
