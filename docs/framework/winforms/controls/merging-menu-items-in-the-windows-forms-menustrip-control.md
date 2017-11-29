---
title: Mesclando itens de menu no controle MenuStrip dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8e042b3f7b0a2a2e40b8fba33fca6c147086df6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>Mesclando itens de menu no controle MenuStrip dos Windows Forms
Se tiver um aplicativo de interface MDI, você poderá mesclar os itens de menu ou os menus inteiros do formulário filho com os menus do formulário pai.  
  
 Este tópico descreve os conceitos básicos associados aos itens de menu de mesclagem em um aplicativo MDI.  
  
## <a name="general-concepts"></a>Conceitos gerais  
 Os procedimentos de mesclagem envolvem um controle do código-fonte e de destino:  
  
-   O destino é o <xref:System.Windows.Forms.MenuStrip> controle do formulário pai MDI ou o principal no qual você estiver mesclando itens de menu.  
  
-   A fonte é o <xref:System.Windows.Forms.MenuStrip> controle no formulário filho MDI que contém os itens de menu que você deseja mesclar com o menu de destino.  
  
 O <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriedade identifica o item de menu filho do formulário MDI pai dos cuja lista suspensa será populado com os títulos do MDI atual. Por exemplo, você normalmente lista o filho MDI que está aberto no momento no menu **Janela**.  
  
 O <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A> propriedade identifica quais itens de menu vêm de um <xref:System.Windows.Forms.MenuStrip> em um formulário MDI filho.  
  
 Você pode mesclar itens de menu de forma manual ou automática. Os itens de menu são mesclados da mesma maneira para os dois métodos, mas a mesclagem é ativada de forma diferente, conforme discutido nas seções "Mesclagem manual" e "Mesclagem automática" neste tópico. Tanto na mesclagem manual quanto na automática, cada ação de mesclagem afeta a próxima.  
  
 <xref:System.Windows.Forms.MenuStrip>Mesclando move itens de menu de um <xref:System.Windows.Forms.ToolStrip> para outro, em vez de clonagem, como era o caso com <xref:System.Windows.Forms.MainMenu>.  
  
## <a name="mergeaction-values"></a>Valores de MergeAction  
 Definir a ação de mesclagem em itens de menu na fonte de <xref:System.Windows.Forms.MenuStrip> usando o <xref:System.Windows.Forms.MergeAction> propriedade.  
  
 A tabela a seguir descreve o significado e o uso típico das ações de mesclagem disponíveis.  
  
|Valor de MergeAction|Descrição|Uso típico|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|(Padrão) Adiciona o item de origem ao final da coleção do item de destino.|Adicionar itens de menu no final do menu quando alguma parte do programa é ativada.|  
|<xref:System.Windows.Forms.MergeAction.Insert>|Adiciona o item de origem à coleção do item de destino, no local especificado pelo <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> propriedade definida no item de origem.|Adicionar itens de menu no início ou no meio do menu quando alguma parte do programa é ativada.<br /><br /> Se o valor de <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> é o mesmo para ambos os itens de menu, eles são adicionados na ordem inversa. Definir <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> adequadamente para preservar a ordem original.|  
|<xref:System.Windows.Forms.MergeAction.Replace>|Localiza uma correspondência de texto, ou usa o <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> valor se nenhuma correspondência de texto for encontrada e, em seguida, substitui o item de menu do destino correspondente com o item de menu de origem.|Substituir um item de menu de destino por um item de menu de origem de mesmo nome que faz algo diferente.|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|Localiza uma correspondência de texto, ou usa o <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> valor se nenhuma correspondência de texto for encontrada e, em seguida, adiciona todos os itens de menu suspenso da origem para o destino.|Criar uma estrutura de menu que insere ou adiciona itens de menu em um submenu ou remove itens de menu de um submenu. Por exemplo, você pode adicionar um item de menu de um filho MDI um principal <xref:System.Windows.Forms.MenuStrip> **Salvar como** menu.<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly>permite navegar pela estrutura de menu sem realizar nenhuma ação. Ele fornece uma maneira de avaliar os itens subsequentes.|  
|<xref:System.Windows.Forms.MergeAction.Remove>|Localiza uma correspondência de texto, ou usa o <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> valor se nenhuma correspondência de texto for encontrada e, em seguida, remove o item de destino.|Remover um item de menu do destino <xref:System.Windows.Forms.MenuStrip>.|  
  
## <a name="manual-merging"></a>Manual de mesclagem  
 Somente <xref:System.Windows.Forms.MenuStrip> controles participarem da mesclagem automática. Para combinar os itens de outros controles, como <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.StatusStrip> controles, você deve mesclá-los manualmente, chamando o <xref:System.Windows.Forms.ToolStripManager.Merge%2A> e <xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A> métodos em seu código conforme necessário.  
  
## <a name="automatic-merging"></a>Mesclagem automática  
 Você pode usar a mesclagem automática para aplicativos MDI, ativando o formulário de origem. Para usar um <xref:System.Windows.Forms.MenuStrip> em um aplicativo MDI, defina o <xref:System.Windows.Forms.Form.MainMenuStrip%2A> propriedade para o destino <xref:System.Windows.Forms.MenuStrip> para que a mesclagem de ações executadas na fonte de <xref:System.Windows.Forms.MenuStrip> são refletidas no destino <xref:System.Windows.Forms.MenuStrip>.  
  
 Você pode disparar uma mesclagem automática ativando o <xref:System.Windows.Forms.MenuStrip> na fonte de MDI. Após a ativação, a fonte <xref:System.Windows.Forms.MenuStrip> é mesclado no destino MDI. Quando um novo formulário se torna ativo, a mesclagem é revertida no último formulário e acionada no novo formulário. Você pode controlar esse comportamento, definindo a <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> propriedade conforme necessário em cada <xref:System.Windows.Forms.ToolStripItem>e definindo a <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> propriedade em cada <xref:System.Windows.Forms.MenuStrip>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.MenuStrip>  
 [Controle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [Como criar uma lista de janelas MDI com MenuStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)  
 [Como configurar a mesclagem de menu automática para aplicativos MDI](../../../../docs/framework/winforms/controls/how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
