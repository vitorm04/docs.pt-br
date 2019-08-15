---
title: 'Como: Habilitar exibição lado a lado em um controle ListView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 8a45a8a484bd373f53585b1b113a51e59b30fca2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040358"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Como: Habilitar exibição lado a lado em um controle ListView do Windows Forms usando o designer
O recurso de exibição de bloco <xref:System.Windows.Forms.ListView> do controle permite que você forneça um equilíbrio visual entre informações gráficas e textuais. As informações textuais exibidas para um item na exibição lado a lado são as mesmas que as informações de coluna definidas para exibição de detalhes. As funções de exibição de bloco em combinação com os recursos de agrupamento ou marca <xref:System.Windows.Forms.ListView> de inserção no controle.

 O modo de exibição lado a lado usa um ícone de 32 x 32 e várias linhas de texto, conforme mostrado na imagem a seguir.

 ![Exibição de bloco em um controle ListView](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Texto e ícones de exibição de bloco")

 Propriedades e métodos de exibição lado a lado permitem especificar quais campos de coluna devem ser exibidos para cada item e controlar coletivamente o tamanho e a aparência de todos os itens dentro de uma janela de exibição lado a lado. Para maior clareza, a primeira linha do texto em uma exibição lado a lado é sempre o nome do item; isso não pode ser alterado.

 O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.ListView> formulário que contém um controle. Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).

> [!NOTE]
> A exibição de bloco está disponível somente [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] em quando o aplicativo chama <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> o método. Em sistemas operacionais anteriores, qualquer código relacionado à exibição de bloco não tem nenhum efeito e o <xref:System.Windows.Forms.ListView> controle é exibido na exibição de ícones grandes. Para obter mais informações, consulte <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.

## <a name="to-set-tile-view-in-the-designer"></a>Para definir a exibição lado a lado no designer

1. No Visual Studio, selecione o <xref:System.Windows.Forms.ListView> controle no formulário.

2. Na janela **Propriedades** , selecione a <xref:System.Windows.Forms.ListView.View%2A> Propriedade e escolha **bloco**.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [Visão geral do controle ListView](listview-control-overview-windows-forms.md)
