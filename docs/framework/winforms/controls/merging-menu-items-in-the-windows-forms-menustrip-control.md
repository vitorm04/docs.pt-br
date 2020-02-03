---
title: Mesclando itens de menu no controle MenuStrip
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
ms.openlocfilehash: 9fc2b40ef23d72db51853c124095b734a7646cda
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739047"
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>Mesclando itens de menu no controle MenuStrip dos Windows Forms
Se tiver um aplicativo de interface MDI, você poderá mesclar os itens de menu ou os menus inteiros do formulário filho com os menus do formulário pai.  
  
 Este tópico descreve os conceitos básicos associados aos itens de menu de mesclagem em um aplicativo MDI.  
  
## <a name="general-concepts"></a>Conceitos gerais  
 Os procedimentos de mesclagem envolvem um controle do código-fonte e de destino:  
  
- O destino é o controle <xref:System.Windows.Forms.MenuStrip> no formulário pai principal ou MDI ao qual você está mesclando itens de menu.  
  
- A origem é o controle <xref:System.Windows.Forms.MenuStrip> no formulário filho MDI que contém os itens de menu que você deseja mesclar no menu de destino.  
  
 A propriedade <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> identifica o item de menu cuja lista suspensa você preencherá com os títulos dos filhos MDI do formulário pai MDI atual. Por exemplo, você normalmente lista o filho MDI que está aberto no momento no menu **Janela**.  
  
 A propriedade <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A> identifica quais itens de menu são provenientes de um <xref:System.Windows.Forms.MenuStrip> em um formulário filho MDI.  
  
 Você pode mesclar itens de menu de forma manual ou automática. Os itens de menu são mesclados da mesma maneira para os dois métodos, mas a mesclagem é ativada de forma diferente, conforme discutido nas seções "Mesclagem manual" e "Mesclagem automática" neste tópico. Tanto na mesclagem manual quanto na automática, cada ação de mesclagem afeta a próxima.  
  
 <xref:System.Windows.Forms.MenuStrip> mesclagem move itens de menu de um <xref:System.Windows.Forms.ToolStrip> para outro em vez de cloná-los, como era o caso com <xref:System.Windows.Forms.MainMenu>.  
  
## <a name="mergeaction-values"></a>Valores de MergeAction  
 Você define a ação de mesclagem em itens de menu no <xref:System.Windows.Forms.MenuStrip> de origem usando a propriedade <xref:System.Windows.Forms.MergeAction>.  
  
 A tabela a seguir descreve o significado e o uso típico das ações de mesclagem disponíveis.  
  
|Valor de MergeAction|Descrição|Usos comum|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|(Padrão) Adiciona o item de origem ao final da coleção do item de destino.|Adicionar itens de menu no final do menu quando alguma parte do programa é ativada.|  
|<xref:System.Windows.Forms.MergeAction.Insert>|Adiciona o item de origem à coleção do item de destino, no local especificado pela propriedade <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> definida no item de origem.|Adicionar itens de menu no início ou no meio do menu quando alguma parte do programa é ativada.<br /><br /> Se o valor de <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> for o mesmo para ambos os itens de menu, eles serão adicionados na ordem inversa. Defina <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> adequadamente para preservar o pedido original.|  
|<xref:System.Windows.Forms.MergeAction.Replace>|Localiza uma correspondência de texto ou usa o valor <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> se nenhuma correspondência de texto for encontrada e, em seguida, substituir o item de menu de destino correspondente pelo item de menu de origem.|Substituir um item de menu de destino por um item de menu de origem de mesmo nome que faz algo diferente.|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|Localiza uma correspondência de texto, ou usa o valor <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> se nenhuma correspondência de texto for encontrada e, em seguida, adiciona todos os itens suspensos da origem ao destino.|Criar uma estrutura de menu que insere ou adiciona itens de menu em um submenu ou remove itens de menu de um submenu. Por exemplo, você pode adicionar um item de menu de um filho MDI a um menu principal <xref:System.Windows.Forms.MenuStrip>**salvar como** .<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly> permite que você navegue pela estrutura do menu sem realizar nenhuma ação. Ele fornece uma maneira de avaliar os itens subsequentes.|  
|<xref:System.Windows.Forms.MergeAction.Remove>|Localiza uma correspondência de texto ou usa o valor <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> se nenhuma correspondência de texto for encontrada e, em seguida, remove o item do destino.|Removendo um item de menu do <xref:System.Windows.Forms.MenuStrip>de destino.|  
  
## <a name="manual-merging"></a>Manual de mesclagem  
 Somente <xref:System.Windows.Forms.MenuStrip> controles participam da mesclagem automática. Para combinar os itens de outros controles, como <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.StatusStrip> controles, você deve mesclá-los manualmente, chamando os métodos <xref:System.Windows.Forms.ToolStripManager.Merge%2A> e <xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A> em seu código, conforme necessário.  
  
## <a name="automatic-merging"></a>Mesclagem automática  
 Você pode usar a mesclagem automática para aplicativos MDI, ativando o formulário de origem. Para usar um <xref:System.Windows.Forms.MenuStrip> em um aplicativo MDI, defina a propriedade <xref:System.Windows.Forms.Form.MainMenuStrip%2A> para o <xref:System.Windows.Forms.MenuStrip> de destino para que as ações de mesclagem executadas no <xref:System.Windows.Forms.MenuStrip> de origem sejam refletidas na <xref:System.Windows.Forms.MenuStrip>de destino.  
  
 Você pode disparar a mesclagem automática ativando o <xref:System.Windows.Forms.MenuStrip> na origem MDI. Após a ativação, o <xref:System.Windows.Forms.MenuStrip> de origem é mesclado no destino MDI. Quando um novo formulário se torna ativo, a mesclagem é revertida no último formulário e acionada no novo formulário. Você pode controlar esse comportamento definindo a propriedade <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> conforme necessário em cada <xref:System.Windows.Forms.ToolStripItem>e definindo a propriedade <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> em cada <xref:System.Windows.Forms.MenuStrip>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- [Controle MenuStrip](menustrip-control-windows-forms.md)
- [Como criar uma lista de janelas MDI com MenuStrip](how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)
- [Como configurar a mesclagem de menu automática para aplicativos MDI](how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
