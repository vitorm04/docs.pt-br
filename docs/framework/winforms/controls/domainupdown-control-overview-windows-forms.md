---
title: Visão geral do controle DomainUpDown
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 86703a96d4845414d043161e0efa67bfde9278db
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745864"
---
# <a name="domainupdown-control-overview-windows-forms"></a>Visão geral do controle DomainUpDown (Windows Forms)
O controle de <xref:System.Windows.Forms.DomainUpDown> de Windows Forms é essencialmente uma combinação de uma caixa de texto e um par de botões para mover para cima ou para baixo através de uma lista. O controle exibe e define uma sequências de texto em uma lista de escolhas. O usuário pode selecionar a sequência clicando nos botões para cima e para baixo para mover a lista, apertando as teclas de direção PARA BAIXO e PARA CIMA ou digitando uma cadeia de caracteres que corresponda a um item na lista. Um possível uso para este controle é selecionar itens de uma lista de nomes ordenada alfabeticamente.  
  
> [!NOTE]
> Para classificar a lista, defina a propriedade <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> como `true`.  
  
 A função deste controle é bem parecida com a da caixa de listagem ou caixa de combinação, mas ocupa muito pouco espaço.  
  
## <a name="key-properties"></a>Propriedades da chave  
 As propriedades de chave do controle são <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>e <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. A propriedade <xref:System.Windows.Forms.DomainUpDown.Items%2A> contém a lista de objetos cujos valores de texto são exibidos no controle. Se <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> for definido como `false`, o controle concluirá automaticamente o texto que o usuário digita e faz a correspondência com um valor na lista. Se <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> for definido como `true`, a rolagem após o último item levará você para o primeiro item na lista e vice-versa. Os principais métodos do controle são <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> e <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Este controle exibe somente sequências de texto. Se você quiser um controle que exiba valores numéricos, use o controle <xref:System.Windows.Forms.NumericUpDown>. Para mais informação, consulte [Visão geral do controle NumericUpDown](numericupdown-control-overview-windows-forms.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DomainUpDown>
- [Controle DomainUpDown](domainupdown-control-windows-forms.md)
