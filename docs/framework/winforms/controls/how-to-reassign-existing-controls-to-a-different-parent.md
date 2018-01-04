---
title: Como reatribuir controles existentes a um pai diferente
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3186dcf3b1f56799709f1e1976a55288065352b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Como reatribuir controles existentes a um pai diferente
Você pode atribuir controles que existem em seu formulário para um novo controle de contêiner.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a>Para reatribuir controles existentes a um pai diferente  
  
1.  Arraste três <xref:System.Windows.Forms.Button> controla a partir de **caixa de ferramentas** para o formulário.  
  
     Posicione-os próximo entre si, mas deixe-os desalinhados.  
  
2.  No **caixa de ferramentas**, clique no <xref:System.Windows.Forms.FlowLayoutPanel> ícone do controle.  
  
     Não arraste o ícone para o formulário.  
  
3.  Mova o ponteiro do mouse perto de três <xref:System.Windows.Forms.Button> controles.  
  
     O ponteiro mudar para uma cruz com o <xref:System.Windows.Forms.FlowLayoutPanel> ícone de controle.  
  
4.  Clique e mantenha o botão do mouse pressionado.  
  
5.  Arraste o ponteiro do mouse para desenhar o contorno do <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
6.  Desenhar o contorno em torno de três <xref:System.Windows.Forms.Button> controles.  
  
7.  Solte o botão do mouse.  
  
     Os três <xref:System.Windows.Forms.Button> controles agora são inseridos a <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Organizando Controles nos Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Instruções passo a passo: organizando controles no Windows Forms usando guias de alinhamento](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
