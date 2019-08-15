---
title: 'Como: Criar uma interface no estilo do Windows Explorer em Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: db2c5431dfb0156c1508a18ef13d2af80eb4981b
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039528"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>Como: Criar uma interface no estilo do Windows Explorer em Windows Forms
O Windows Explorer é uma opção de interface do usuário comum para aplicativos devido à sua familiaridade pronta.

 O Windows Explorer é, essencialmente, <xref:System.Windows.Forms.TreeView> um controle e <xref:System.Windows.Forms.ListView> um controle em painéis separados. Os painéis são redimensionáveis por um divisor. Essa disposição de controles é muito eficiente para exibir e procurar informações.

 As etapas a seguir mostram como organizar controles em um formato semelhante ao Windows Explorer. Elas não mostram como adicionar a funcionalidade de localização de arquivos do aplicativo Windows Explorer.

## <a name="to-create-a-windows-explorer-style-windows-form"></a>Para criar um Windows Form no estilo do Windows Explorer

1. Criar um novo projeto de aplicativo do Windows (**arquivo** > **novo** > **projeto** > **Visual C#**  ou **Visual Basic** > **área de trabalho clássica**  >  **Windows Forms aplicativo**).

2. Na **Caixa de Ferramentas**:

    1. Arraste um <xref:System.Windows.Forms.SplitContainer> controle para o formulário.

    2. Arraste um <xref:System.Windows.Forms.TreeView> controle para **SplitterPanel1** ( <xref:System.Windows.Forms.SplitContainer> o painel do controle marcado como **Panel1**).

    3. Arraste um <xref:System.Windows.Forms.ListView> controle para **SplitterPanel2** ( <xref:System.Windows.Forms.SplitContainer> o painel do controle marcado como **Panel2**).

3. Selecione os três controles pressionando a tecla CTRL e clicando neles. Ao selecionar o <xref:System.Windows.Forms.SplitContainer> controle, clique na barra de divisão, em vez de nos painéis.

    > [!NOTE]
    >  Não use o comando **Selecionar Tudo** no menu **Editar**. Se você fizer isso, a propriedade necessária na próxima etapa não aparecerá na janela **Propriedades**.

4. Na janela **Propriedades** , defina a <xref:System.Windows.Forms.SplitContainer.Dock%2A> Propriedade como <xref:System.Windows.Forms.DockStyle.Fill>.

5. Pressione F5 para executar o aplicativo.

     O formulário exibe uma interface do usuário de duas partes, semelhante à do Windows Explorer.

    > [!NOTE]
    >  Quando você arrasta o divisor, os painéis são redimensionados.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.SplitContainer>
- [Como: Criar uma interface do usuário multipainel com Windows Forms](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [Como: Definir o comportamento de redimensionamento e posicionamento em uma janela de divisão](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [Como: Dividir uma janela horizontalmente](how-to-split-a-window-horizontally.md)
- [Controle SplitContainer](splitcontainer-control-windows-forms.md)
