---
title: 'Como: Transferir controles existentes a um pai diferente'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 84e662e0bd2689115abe128c6442e4462eed3e18
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987034"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Como: Reatribuir controles existentes a um pai diferente

Você pode atribuir controles que existem no formulário a um novo controle de contêiner.

1. No Visual Studio, arraste três <xref:System.Windows.Forms.Button> controles da **caixa de ferramentas** para o formulário. Posicione-os próximo entre si, mas deixe-os desalinhados.

2. Na **caixa de ferramentas**, clique <xref:System.Windows.Forms.FlowLayoutPanel> no ícone de controle. (Não arraste o ícone para o formulário.)

3. Mova o ponteiro do mouse para perto dos <xref:System.Windows.Forms.Button> três controles.

   O ponteiro muda para um cruzado com <xref:System.Windows.Forms.FlowLayoutPanel> o ícone de controle anexado.

4. Clique e mantenha o botão do mouse pressionado.

5. Arraste o ponteiro do mouse para desenhar a estrutura de <xref:System.Windows.Forms.FlowLayoutPanel> tópicos do controle.

6. Desenhe a estrutura de tópicos em <xref:System.Windows.Forms.Button> torno dos três controles.

7. Solte o botão do mouse.

   Os três <xref:System.Windows.Forms.Button> controles agora são inseridos <xref:System.Windows.Forms.FlowLayoutPanel> no controle.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Passo a passo: Organizando controles em Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Passo a passo: Organizando controles em Windows Forms usando Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
