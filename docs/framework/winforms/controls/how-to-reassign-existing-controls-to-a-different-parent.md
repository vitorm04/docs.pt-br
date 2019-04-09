---
title: 'Como: Transferir controles existentes a um pai diferente'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: 113afc642ca313f10062a496d2f170e3666d5043
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162235"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Como: Transferir controles existentes a um pai diferente
Você pode atribuir controles existentes em seu formulário para um novo controle de contêiner.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a>Para reatribuir controles existentes a um pai diferente  
  
1.  Arraste três <xref:System.Windows.Forms.Button> controla a partir de **caixa de ferramentas** para o formulário.  
  
     Posicione-os próximo entre si, mas deixe-os desalinhados.  
  
2.  No **caixa de ferramentas**, clique no <xref:System.Windows.Forms.FlowLayoutPanel> ícone do controle.  
  
     Arraste o ícone para o formulário.  
  
3.  Mova o ponteiro do mouse perto de três <xref:System.Windows.Forms.Button> controles.  
  
     O ponteiro muda para uma mira com o <xref:System.Windows.Forms.FlowLayoutPanel> ícone do controle anexado.  
  
4.  Clique e mantenha o botão do mouse pressionado.  
  
5.  Arraste o ponteiro do mouse para desenhar o contorno do <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
6.  Desenhar o contorno em torno de três <xref:System.Windows.Forms.Button> controles.  
  
7.  Solte o botão do mouse.  
  
     Os três <xref:System.Windows.Forms.Button> controles agora são inseridos no <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Organizando controles nos Windows Forms](arranging-controls-on-windows-forms.md)
- [Passo a passo: Organizar controles nos Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Passo a passo: Organizar controles nos Windows Forms usando linhas de alinhamento](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
