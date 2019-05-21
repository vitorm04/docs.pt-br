---
title: 'Como: Adicionar ou remover imagens ImageList com o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: 57c124f19d208192cb2d4500274f7f897948252a
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960159"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a>Como: Adicionar ou remover imagens ImageList com o Designer

Você pode adicionar imagens a um <xref:System.Windows.Forms.ImageList> componente de várias maneiras diferentes. Você pode adicionar imagens rapidamente usando a smart tag associada a <xref:System.Windows.Forms.ImageList>, ou se você estiver configurando várias outras propriedades do <xref:System.Windows.Forms.ImageList>, talvez seja mais conveniente para adicionar imagens com a janela Propriedades. Também é possível adicionar imagens usando o código. Para obter mais informações sobre como adicionar imagens com o código, consulte [como: Adicionar ou remover imagens com o Windows Forms componente ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md). Normalmente, você preenche o <xref:System.Windows.Forms.ImageList> componente com imagens antes que ele está associado com um controle, mas isso não é necessário.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a>Para adicionar ou remover imagens usando a janela Propriedades

1. Selecione o <xref:System.Windows.Forms.ImageList> componente, ou adicionar um ao formulário.

2. Na janela Propriedades, clique no botão de reticências (![botão do botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado de <xref:System.Windows.Forms.ImageList.Images%2A> propriedade.

3. No **Editor de coleção de imagens**, clique em **Adicionar** ou **Remover** para adicionar ou remover imagens da lista.

### <a name="to-add-or-remove-images-using-the-smart-tag"></a>Para adicionar ou remover imagens usando a smart tag

1. Selecione o <xref:System.Windows.Forms.ImageList> componente, ou adicionar um ao formulário.

2. Clique no glifo de smart tag (![Glifo de smart tag](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))

3. Na caixa de diálogo **Tarefas ImageList**, selecione **Escolher imagens**.

4. No **Editor de coleção de imagens**, clique em **Adicionar** ou **Remover** para adicionar ou remover imagens da lista.

## <a name="see-also"></a>Consulte também

- [Imagens, bitmaps e metarquivos](../advanced/images-bitmaps-and-metafiles.md)
- [Passo a passo: Realizando tarefas comuns usando Smart Tags no Windows, controles de formulários](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [Componente ImageList](imagelist-component-windows-forms.md)
