---
title: Como habilitar exibição lado a lado em um controle ListView dos Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 4f51d3a596bc3358942cdfd654b3e4515d96cd07
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960106"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Como habilitar exibição lado a lado em um controle ListView dos Windows Forms usando o designer
O recurso de exibição de bloco do controle de <xref:System.Windows.Forms.ListView> permite que você forneça um equilíbrio visual entre informações gráficas e textuais. As informações textuais exibidas para um item na exibição lado a lado são as mesmas que as informações de coluna definidas para exibição de detalhes. As funções de exibição de bloco em combinação com os recursos de agrupamento ou marca de inserção no controle de <xref:System.Windows.Forms.ListView>.

 O modo de exibição lado a lado usa um ícone de 32 x 32 e várias linhas de texto, conforme mostrado na imagem a seguir.

 ![Exibição lado a lado em um controle ListView](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Ícones e texto da exibição lado a lado")

 Propriedades e métodos de exibição lado a lado permitem especificar quais campos de coluna devem ser exibidos para cada item e controlar coletivamente o tamanho e a aparência de todos os itens dentro de uma janela de exibição lado a lado. Para maior clareza, a primeira linha do texto em uma exibição lado a lado é sempre o nome do item; isso não pode ser alterado.

 O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.ListView>. Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-set-tile-view-in-the-designer"></a>Para definir a exibição lado a lado no designer

1. No Visual Studio, selecione o controle de <xref:System.Windows.Forms.ListView> no formulário.

2. Na janela **Propriedades** , selecione a propriedade <xref:System.Windows.Forms.ListView.View%2A> e escolha **bloco**.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [Visão geral do controle ListView](listview-control-overview-windows-forms.md)
