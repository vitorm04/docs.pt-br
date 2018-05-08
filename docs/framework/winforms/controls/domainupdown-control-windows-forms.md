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
ms.openlocfilehash: c23f374f1ec9cab6e43b12d32b97c40533ac36cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="domainupdown-control-windows-forms"></a>Controle DomainUpDown (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DomainUpDown> controle parece com uma combinação de uma caixa de texto e um par de botões para mover para cima ou para baixo em uma lista. O controle exibe e define uma sequências de texto em uma lista de escolhas. O usuário pode selecionar a sequência clicando nos botões para cima e para baixo para mover a lista, apertando as teclas de direção PARA BAIXO e PARA CIMA ou digitando uma cadeia de caracteres que corresponda a um item na lista. Um possível uso para este controle é selecionar itens de uma lista de nomes ordenada alfabeticamente. (Para classificar a lista, defina o <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> propriedade `true`.) A função deste controle é bem parecida com a da caixa de listagem ou caixa de combinação, mas ocupa muito pouco espaço.  
  
 As propriedades de chave do controle são <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, e <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. O <xref:System.Windows.Forms.DomainUpDown.Items%2A> propriedade contém a lista de objetos cujos valores de texto são exibidos no controle. Se <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> é definido como `false`, o controle preenche automaticamente o texto que o usuário digita e faz a correspondência com um valor na lista. Se <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> é definido como `true`, após o último item de rolagem levará você para o primeiro item na lista e vice-versa. Os métodos de chave do controle são <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> e <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Este controle exibe somente sequências de texto. Se você quiser um controle que exibe valores numéricos, use o <xref:System.Windows.Forms.NumericUpDown> controle. Para obter mais informações, consulte [controle NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md) .  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral do controle DomainUpDown](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)  
 Apresenta os conceitos gerais do <xref:System.Windows.Forms.DomainUpDown> controle, que permite aos usuários procurar e selecionar em uma lista de cadeias de caracteres de texto.  
  
 [How to: Add Items to Windows Forms DomainUpDown Controls Programmatically](../../../../docs/framework/winforms/controls/how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md) (Como adicionar itens nos controles DomainUpDown dos Windows Forms de forma programática)  
 Descreve como especificar as cadeias de caracteres de texto a <xref:System.Windows.Forms.DomainUpDown> controle deve exibir.  
  
 [Como remover itens de controles DomainUpDown dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 Descreve como excluir itens do <xref:System.Windows.Forms.DomainUpDown> controle no código.  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.DomainUpDown>  
 Descreve essa classe e tem links para todos os seus membros.  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 Descreve essa classe e tem links para todos os seus membros.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 Fornece uma lista completa dos controles dos Windows Forms, com links para informações sobre seu uso.
