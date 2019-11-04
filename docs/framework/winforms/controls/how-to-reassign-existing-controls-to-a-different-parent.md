---
title: Como reatribuir controles existentes a um pai diferente
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1767fcff1742f4ad630b4b996c709b7ded53a129
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459203"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Como: Reatribuir controles existentes a um pai diferente

Você pode atribuir controles que existem no formulário a um novo controle de contêiner.

1. No Visual Studio, arraste três controles de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para o formulário. Posicione-os próximo entre si, mas deixe-os desalinhados.

2. Na **caixa de ferramentas**, clique no ícone controle de <xref:System.Windows.Forms.FlowLayoutPanel>. (Não arraste o ícone para o formulário.)

3. Mova o ponteiro do mouse para perto dos três <xref:System.Windows.Forms.Button> controles.

   O ponteiro muda para uma cruz com o ícone de controle de <xref:System.Windows.Forms.FlowLayoutPanel> anexado.

4. Clique e mantenha o botão do mouse pressionado.

5. Arraste o ponteiro do mouse para desenhar a estrutura de tópicos do controle de <xref:System.Windows.Forms.FlowLayoutPanel>.

6. Desenhe a estrutura de tópicos em torno dos três controles de <xref:System.Windows.Forms.Button>.

7. Solte o botão do mouse.

   Os três controles de <xref:System.Windows.Forms.Button> agora são inseridos no controle de <xref:System.Windows.Forms.FlowLayoutPanel>.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Instruções passo a passo: organizando controles no Windows Forms usando guias de alinhamento](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
