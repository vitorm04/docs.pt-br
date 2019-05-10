---
title: 'Como: Definir a tela de fundo de um painel do Windows Forms usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 6927a7118c43ced03623a9764a3ef1e0814c95cb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211637"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>Como: Definir plano de fundo de um painel dos Windows Forms usando o Designer

Um Windows Forms <xref:System.Windows.Forms.Panel> controle pode exibir uma cor de fundo e uma imagem de plano de fundo. O <xref:System.Windows.Forms.Control.BackColor%2A> propriedade define a cor de plano de fundo de controles que estão contidos no painel, como rótulos e botões de opção. Se o <xref:System.Windows.Forms.Control.BackgroundImage%2A> não está definida, o <xref:System.Windows.Forms.Control.BackColor%2A> seleção preencherá todos o painel. Se o <xref:System.Windows.Forms.Control.BackgroundImage%2A> estiver definida, a imagem será exibida por trás dos controles que estão contidos no painel.

O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contenha um <xref:System.Windows.Forms.Panel> controle. Para obter informações sobre como configurar um projeto desse tipo no Visual Studio, consulte [como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como: Adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="set-the-background-in-the-windows-forms-designer"></a>Definir o plano de fundo no Designer de formulários do Windows

1. Abra o projeto no Visual Studio e selecione o <xref:System.Windows.Forms.Panel> controle.

2. No **propriedades** , clique na seta ao lado de <xref:System.Windows.Forms.Control.BackColor%2A> propriedade para exibir uma janela com três guias.

3. Selecione a guia **Personalizado** para exibir uma paleta de cores.

4. Selecione a guia **Web** ou **Sistema** para exibir uma lista de nomes predefinidos para cores e, em seguida, selecione uma cor.

5. No **propriedades** , clique na seta ao lado de <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriedade.

6. Na caixa de diálogo **Abrir**, selecione o arquivo que deseja exibir.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Controle de painel](panel-control-windows-forms.md)
- [Visão geral do controle Panel](panel-control-overview-windows-forms.md)
- [Como: Agrupar controles com o controle de painel do Windows Forms usando o Designer](group-controls-with-wf-panel-control-using-the-designer.md)
