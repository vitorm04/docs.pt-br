---
title: Controle DomainUpDown
ms.date: 03/30/2017
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
ms.openlocfilehash: b538350a84e341d6b2759a7db28f8799f3777a86
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745834"
---
# <a name="domainupdown-control-windows-forms"></a>Controle DomainUpDown (Windows Forms)
O controle de <xref:System.Windows.Forms.DomainUpDown> de Windows Forms se parece com uma combinação de uma caixa de texto e um par de botões para mover para cima ou para baixo através de uma lista. O controle exibe e define uma sequências de texto em uma lista de escolhas. O usuário pode selecionar a sequência clicando nos botões para cima e para baixo para mover a lista, apertando as teclas de direção PARA BAIXO e PARA CIMA ou digitando uma cadeia de caracteres que corresponda a um item na lista. Um possível uso para este controle é selecionar itens de uma lista de nomes ordenada alfabeticamente. (Para classificar a lista, defina a propriedade <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> como `true`.) A função desse controle é muito semelhante à caixa de listagem ou caixa de combinação, mas ocupa muito pouco espaço.  
  
 As propriedades de chave do controle são <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>e <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. A propriedade <xref:System.Windows.Forms.DomainUpDown.Items%2A> contém a lista de objetos cujos valores de texto são exibidos no controle. Se <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> for definido como `false`, o controle concluirá automaticamente o texto que o usuário digita e faz a correspondência com um valor na lista. Se <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> for definido como `true`, a rolagem após o último item levará você para o primeiro item na lista e vice-versa. Os principais métodos do controle são <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> e <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Este controle exibe somente sequências de texto. Se você quiser um controle que exiba valores numéricos, use o controle <xref:System.Windows.Forms.NumericUpDown>. Para obter mais informações, consulte o [controle NumericUpDown](numericupdown-control-windows-forms.md) .  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral do controle DomainUpDown](domainupdown-control-overview-windows-forms.md)  
 Apresenta os conceitos gerais do controle de <xref:System.Windows.Forms.DomainUpDown>, que permite aos usuários navegar e selecionar em uma lista de cadeias de caracteres de texto.  
  
 [How to: Add Items to Windows Forms DomainUpDown Controls Programmatically](how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md) (Como adicionar itens nos controles DomainUpDown dos Windows Forms de forma programática)  
 Descreve como especificar as cadeias de caracteres de texto que o controle de <xref:System.Windows.Forms.DomainUpDown> deve exibir.  
  
 [Como remover itens de controles DomainUpDown dos Windows Forms](how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 Descreve como excluir itens do controle de <xref:System.Windows.Forms.DomainUpDown> no código.  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.DomainUpDown>  
 Descreve essa classe e tem links para todos os seus membros.  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 Descreve essa classe e tem links para todos os seus membros.  
  
## <a name="related-sections"></a>Seções Relacionadas  
 [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)  
 Fornece uma lista completa dos controles dos Windows Forms, com links para informações sobre seu uso.
