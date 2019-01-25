---
title: 'Como: Habilitar exibição lado a lado em um controle de ListView do Windows Forms usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 637e11e058a92d7b8df868e8cf9a3cb37e927df5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580119"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Como: Habilitar exibição lado a lado em um controle de ListView do Windows Forms usando o Designer
O recurso de exibição de bloco a <xref:System.Windows.Forms.ListView> controle permite que você fornecer um equilíbrio visual entre informações gráficas e textuais. As informações textuais exibidas para um item na exibição lado a lado são as mesmas que as informações de coluna definidas para exibição de detalhes. Funções de exibição lado a lado em combinação com o agrupamento ou inserção recursos de marca no <xref:System.Windows.Forms.ListView> controle.  
  
 O modo de exibição lado a lado usa um ícone de 32 x 32 e várias linhas de texto, conforme mostrado na imagem a seguir.  
  
 ![Exibição lado a lado em um controle ListView](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")  
  
 Propriedades e métodos de exibição lado a lado permitem especificar quais campos de coluna devem ser exibidos para cada item e controlar coletivamente o tamanho e a aparência de todos os itens dentro de uma janela de exibição lado a lado. Para maior clareza, a primeira linha do texto em uma exibição lado a lado é sempre o nome do item; isso não pode ser alterado.  
  
 O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.ListView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [como: Criar um projeto de aplicativo do Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [como: Adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  A exibição lado a lado está disponível apenas no [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] quando seu aplicativo chama o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método. Em sistemas operacionais anteriores, qualquer código relacionado ao modo de exibição lado a lado não terá efeito e o <xref:System.Windows.Forms.ListView> controle exibe no modo de exibição de ícones grandes. Para obter mais informações, consulte <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
>   
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-tile-view-in-the-designer"></a>Para definir a exibição lado a lado no designer  
  
1.  Selecione o <xref:System.Windows.Forms.ListView> controle no formulário.  
  
2.  No **propriedades** janela, selecione a <xref:System.Windows.Forms.ListView.View%2A> propriedade e escolha **bloco**.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [Recursos do Windows XP e controles do Windows Forms](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)
- [Visão geral do controle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
