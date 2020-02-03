---
title: Definir o plano de fundo de um painel usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 8bdefba433632f7ba02f549a549c52c7aa56c2d7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731924"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>Como: definir o plano de fundo de um painel de Windows Forms usando o designer

Um controle de <xref:System.Windows.Forms.Panel> de Windows Forms pode exibir uma cor de plano de fundo e uma imagem de plano de fundo. A propriedade <xref:System.Windows.Forms.Control.BackColor%2A> define a cor do plano de fundo dos controles contidos no painel, como rótulos e botões de opção. Se a propriedade <xref:System.Windows.Forms.Control.BackgroundImage%2A> não estiver definida, a seleção de <xref:System.Windows.Forms.Control.BackColor%2A> preencherá todo o painel. Se a propriedade <xref:System.Windows.Forms.Control.BackgroundImage%2A> for definida, a imagem será exibida atrás dos controles contidos no painel.

O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contenha um controle de <xref:System.Windows.Forms.Panel>. Para obter informações sobre como configurar esse projeto no Visual Studio, consulte [como criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como: adicionar controles a Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="set-the-background-in-the-windows-forms-designer"></a>Definir o plano de fundo no Designer de Formulários do Windows

1. Abra o projeto no Visual Studio e selecione o controle de <xref:System.Windows.Forms.Panel>.

2. Na janela **Propriedades** , clique no botão de seta ao lado da propriedade <xref:System.Windows.Forms.Control.BackColor%2A> para exibir uma janela com três guias.

3. Selecione a guia **Personalizado** para exibir uma paleta de cores.

4. Selecione a guia **Web** ou **Sistema** para exibir uma lista de nomes predefinidos para cores e, em seguida, selecione uma cor.

5. Na janela **Propriedades** , clique no botão de seta ao lado da propriedade <xref:System.Windows.Forms.Control.BackgroundImage%2A>.

6. Na caixa de diálogo **Abrir**, selecione o arquivo que deseja exibir.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Controle de painel](panel-control-windows-forms.md)
- [Visão geral do controle Panel](panel-control-overview-windows-forms.md)
- [Como agrupar controles com o controle de painel dos Windows Forms usando o Designer](group-controls-with-wf-panel-control-using-the-designer.md)
