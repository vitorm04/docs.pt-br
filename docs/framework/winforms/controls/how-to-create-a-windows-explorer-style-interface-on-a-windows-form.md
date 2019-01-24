---
title: 'Como: Criar uma Interface no estilo Explorer do Windows em um formulário do Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 0b61961aff04a089ce12f4b96637e3f05023e929
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511089"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>Como: Criar uma Interface no estilo Explorer do Windows em um formulário do Windows
O Windows Explorer é uma opção de interface do usuário comum para aplicativos devido à sua familiaridade pronta.  
  
 Windows Explorer é, essencialmente, uma <xref:System.Windows.Forms.TreeView> controle e um <xref:System.Windows.Forms.ListView> controle em painéis separados. Os painéis são redimensionáveis por um divisor. Essa disposição de controles é muito eficiente para exibir e procurar informações.  
  
 As etapas a seguir mostram como organizar controles em um formato semelhante ao Windows Explorer. Elas não mostram como adicionar a funcionalidade de localização de arquivos do aplicativo Windows Explorer.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a>Para criar um Windows Form no estilo do Windows Explorer  
  
1.  Criar um novo projeto de aplicativo do Windows (**arquivo** > **New** > **projeto** > **Visual C#** ou **Visual Basic** > **área de trabalho clássica** > **aplicativo de formulários do Windows**).  
  
2.  Na **Caixa de Ferramentas**:  
  
    1.  Arraste um <xref:System.Windows.Forms.SplitContainer> controle para seu formulário.  
  
    2.  Arraste uma <xref:System.Windows.Forms.TreeView> controlar em **SplitterPanel1** (o painel do <xref:System.Windows.Forms.SplitContainer> controle marcado **Painel1**).  
  
    3.  Arraste uma <xref:System.Windows.Forms.ListView> controlar em **SplitterPanel2** (o painel do <xref:System.Windows.Forms.SplitContainer> controle marcado **Painel2**).  
  
3.  Selecione os três controles pressionando a tecla CTRL e clicando neles. Quando você seleciona o <xref:System.Windows.Forms.SplitContainer> de controle, clique na barra de divisão, em vez dos painéis.  
  
    > [!NOTE]
    >  Não use o comando **Selecionar Tudo** no menu **Editar**. Se você fizer isso, a propriedade necessária na próxima etapa não aparecerá na janela **Propriedades**.  
  
4.  No **propriedades** janela, defina as <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>.  
  
5.  Pressione F5 para executar o aplicativo.  
  
     O formulário exibe uma interface do usuário de duas partes, semelhante à do Windows Explorer.  
  
    > [!NOTE]
    >  Quando você arrasta o divisor, os painéis são redimensionados.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.SplitContainer>
- [Como: Criar uma Interface do usuário Multipainel com Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [Como: Definir redimensionamento e posicionamento de comportamento em uma janela dividida](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [Como: Dividir uma janela horizontalmente](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)
- [Controle SplitContainer](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
