---
title: Visão geral do controle DomainUpDown (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: bfe3e7239f77c6f1a0d9bb46a96c704653b43364
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102850"
---
# <a name="domainupdown-control-overview-windows-forms"></a>Visão geral do controle DomainUpDown (Windows Forms)
Os formulários do Windows <xref:System.Windows.Forms.DomainUpDown> controle é essencialmente uma combinação de uma caixa de texto e um par de botões para mover para cima ou para baixo através de uma lista. O controle exibe e define uma sequências de texto em uma lista de escolhas. O usuário pode selecionar a sequência clicando nos botões para cima e para baixo para mover a lista, apertando as teclas de direção PARA BAIXO e PARA CIMA ou digitando uma cadeia de caracteres que corresponda a um item na lista. Um possível uso para este controle é selecionar itens de uma lista de nomes ordenada alfabeticamente.  
  
> [!NOTE]
>  Para classificar a lista, defina as <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> propriedade para `true`.  
  
 A função deste controle é bem parecida com a da caixa de listagem ou caixa de combinação, mas ocupa muito pouco espaço.  
  
## <a name="key-properties"></a>Propriedades da chave  
 As principais propriedades do controle são <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, e <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. O <xref:System.Windows.Forms.DomainUpDown.Items%2A> propriedade contém a lista de objetos cujos valores de texto são exibidos no controle. Se <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> é definido como `false`, o controle automaticamente completa o texto que o usuário digita e combina com um valor na lista. Se <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> é definido como `true`, rolagem após o último item você será levado para o primeiro item na lista e vice-versa. Os principais métodos do controle são <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> e <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Este controle exibe somente sequências de texto. Se você quiser um controle que exibe valores numéricos, use o <xref:System.Windows.Forms.NumericUpDown> controle. Para mais informação, consulte [Visão geral do controle NumericUpDown](numericupdown-control-overview-windows-forms.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DomainUpDown>
- [Controle DomainUpDown](domainupdown-control-windows-forms.md)
