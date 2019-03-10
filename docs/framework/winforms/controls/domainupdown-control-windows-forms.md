---
title: Controle DomainUpDown (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
ms.openlocfilehash: 83d674e3fb7ff7e715b75c635b891cd4e9703a21
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704510"
---
# <a name="domainupdown-control-windows-forms"></a>Controle DomainUpDown (Windows Forms)
Os formulários do Windows <xref:System.Windows.Forms.DomainUpDown> controle se parece com uma combinação de uma caixa de texto e um par de botões para mover para cima ou para baixo através de uma lista. O controle exibe e define uma sequências de texto em uma lista de escolhas. O usuário pode selecionar a sequência clicando nos botões para cima e para baixo para mover a lista, apertando as teclas de direção PARA BAIXO e PARA CIMA ou digitando uma cadeia de caracteres que corresponda a um item na lista. Um possível uso para este controle é selecionar itens de uma lista de nomes ordenada alfabeticamente. (Para classificar a lista, defina as <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> propriedade para `true`.) A função deste controle é bem parecida com a da caixa de listagem ou caixa de combinação, mas ocupa muito pouco espaço.  
  
 As principais propriedades do controle são <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, e <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. O <xref:System.Windows.Forms.DomainUpDown.Items%2A> propriedade contém a lista de objetos cujos valores de texto são exibidos no controle. Se <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> é definido como `false`, o controle automaticamente completa o texto que o usuário digita e combina com um valor na lista. Se <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> é definido como `true`, rolagem após o último item você será levado para o primeiro item na lista e vice-versa. Os principais métodos do controle são <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> e <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Este controle exibe somente sequências de texto. Se você quiser um controle que exibe valores numéricos, use o <xref:System.Windows.Forms.NumericUpDown> controle. Para obter mais informações, consulte [controle NumericUpDown](numericupdown-control-windows-forms.md) .  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral do controle DomainUpDown](domainupdown-control-overview-windows-forms.md)  
 Apresenta os conceitos gerais do <xref:System.Windows.Forms.DomainUpDown> controle, que permite que os usuários procurem e selecionem de uma lista de cadeias de caracteres de texto.  
  
 [Como: Adicionar itens a controles DomainUpDown dos Windows Forms por meio de programação](how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 Descreve como especificar as cadeias de caracteres de texto a <xref:System.Windows.Forms.DomainUpDown> controle deve exibir.  
  
 [Como: Remover itens de controles DomainUpDown dos Windows Forms](how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 Descreve como excluir itens do <xref:System.Windows.Forms.DomainUpDown> controle no código.  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.DomainUpDown>  
 Descreve essa classe e tem links para todos os seus membros.  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 Descreve essa classe e tem links para todos os seus membros...  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)  
 Fornece uma lista completa dos controles dos Windows Forms, com links para informações sobre seu uso.
