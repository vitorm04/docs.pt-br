---
title: "Visão geral do controle StatusStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f6d1eb698dbb9168bf5de6d3982e19e69d170ac0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="statusstrip-control-overview"></a>Visão geral do controle StatusStrip
Um <xref:System.Windows.Forms.StatusStrip> controle exibe informações sobre um objeto que está sendo visualizado em um <xref:System.Windows.Forms.Form>, componentes do objeto ou as informações contextuais relacionadas à operação do objeto dentro de seu aplicativo. Normalmente, um <xref:System.Windows.Forms.StatusStrip> consiste em controle <xref:System.Windows.Forms.ToolStripStatusLabel> objetos, cada um deles exibe o texto, um ícone ou ambos. O <xref:System.Windows.Forms.StatusStrip> também podem conter <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, e <xref:System.Windows.Forms.ToolStripProgressBar> controles.  
  
 O padrão <xref:System.Windows.Forms.StatusStrip> não tem nenhum painéis. Para adicionar painéis para um <xref:System.Windows.Forms.StatusStrip>, use o <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> método.  
  
 Há suporte abrangente para manipulação <xref:System.Windows.Forms.StatusStrip> itens e comandos comuns no Visual Studio.  
  
 Consulte também [Editor de coleção de itens StatusStrip](http://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [Caixa de diálogo de tarefas StatusStrip](http://msdn.microsoft.com/library/ms233642\(v=vs.110\)).  
  
 Embora o <xref:System.Windows.Forms.StatusStrip> substitua e estenda o controle <xref:System.Windows.Forms.StatusBar> de versões anteriores, <xref:System.Windows.Forms.StatusBar> é mantido para compatibilidade com versões anteriores e uso futuro, se desejado.  
  
### <a name="important-statusstrip-members"></a>Membros StatusStrip importantes  
  
|Nome|Descrição|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|Obtém ou define um valor que indica se o <xref:System.Windows.Forms.StatusStrip> dá suporte à funcionalidade de estouro.|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|Obtém ou define um valor que indica se o <xref:System.Windows.Forms.StatusStrip> expande de ponta a ponta em seu <xref:System.Windows.Forms.ToolStripContainer>.|  
  
### <a name="important-statusstrip-companion-classes"></a>Classes complementares importantes do StatusStrip  
  
|Nome|Descrição|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Representa um painel em um controle <xref:System.Windows.Forms.StatusStrip>.|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|Exibe um associado <xref:System.Windows.Forms.ToolStripDropDown> do qual o usuário pode selecionar um único item.|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|Representa um controle de duas partes que é um botão padrão e um menu suspenso.|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|Exibe o estado de conclusão de um processo.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
