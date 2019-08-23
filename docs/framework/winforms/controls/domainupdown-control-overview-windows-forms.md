---
title: Visão geral do controle DomainUpDown (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 6fda542204e2b41dd1d729d2b940c6f38a5812ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965307"
---
# <a name="domainupdown-control-overview-windows-forms"></a>Visão geral do controle DomainUpDown (Windows Forms)
O controle <xref:System.Windows.Forms.DomainUpDown> de Windows Forms é essencialmente uma combinação de uma caixa de texto e um par de botões para mover para cima ou para baixo através de uma lista. O controle exibe e define uma sequências de texto em uma lista de escolhas. O usuário pode selecionar a sequência clicando nos botões para cima e para baixo para mover a lista, apertando as teclas de direção PARA BAIXO e PARA CIMA ou digitando uma cadeia de caracteres que corresponda a um item na lista. Um possível uso para este controle é selecionar itens de uma lista de nomes ordenada alfabeticamente.  
  
> [!NOTE]
> Para classificar a lista, defina a <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> Propriedade como `true`.  
  
 A função deste controle é bem parecida com a da caixa de listagem ou caixa de combinação, mas ocupa muito pouco espaço.  
  
## <a name="key-properties"></a>Propriedades da chave  
 As principais propriedades do controle são <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>e <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. A <xref:System.Windows.Forms.DomainUpDown.Items%2A> propriedade contém a lista de objetos cujos valores de texto são exibidos no controle. Se <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> é definido como `false`, o controle completa automaticamente o texto que o usuário digita e faz a correspondência com um valor na lista. Se <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> for definido como `true`, a rolagem após o último item levará você para o primeiro item na lista e vice-versa. Os principais métodos do controle são <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> e. <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>  
  
 Este controle exibe somente sequências de texto. Se você quiser um controle que exiba valores numéricos, use <xref:System.Windows.Forms.NumericUpDown> o controle. Para mais informação, consulte [Visão geral do controle NumericUpDown](numericupdown-control-overview-windows-forms.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DomainUpDown>
- [Controle DomainUpDown](domainupdown-control-windows-forms.md)
