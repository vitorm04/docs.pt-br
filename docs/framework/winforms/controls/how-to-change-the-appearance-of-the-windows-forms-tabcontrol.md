---
title: 'Como: Alterar a aparência do TabControl dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- icons [Windows Forms], displaying on tabs
- TabControl control [Windows Forms], changing page appearance
- tabs [Windows Forms], controlling appearance
- buttons [Windows Forms], displaying tabs as
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
ms.openlocfilehash: 642115eeb61649eb369058947e5347d4389182a0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702406"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>Como: Alterar a aparência do TabControl dos Windows Forms
Você pode alterar a aparência das guias nos Windows Forms usando propriedades do <xref:System.Windows.Forms.TabControl> e o <xref:System.Windows.Forms.TabPage> objetos que compõem guias individuais no controle. Ao configurar essas propriedades, é possível exibir imagens em guias, exibir guias verticalmente em vez de horizontalmente, exibir várias linhas de guias e habilitar ou desabilitar guias com programação.  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>Exibir um ícone na parte de rótulo de uma guia  
  
1.  Adicionar um <xref:System.Windows.Forms.ImageList> controle ao formulário.  
  
2.  Adicione imagens à lista de imagens.  
  
     Para obter mais informações sobre listas de imagens, consulte [componente ImageList](imagelist-component-windows-forms.md) e [como: Adicionar ou remover imagens com o Windows Forms componente ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
3.  Defina a <xref:System.Windows.Forms.TabControl.ImageList%2A> propriedade do <xref:System.Windows.Forms.TabControl> para o <xref:System.Windows.Forms.ImageList> controle.  
  
4.  Defina a <xref:System.Windows.Forms.TabPage.ImageIndex%2A> propriedade do <xref:System.Windows.Forms.TabPage> ao índice de uma imagem apropriada na lista.  
  
### <a name="to-create-multiple-rows-of-tabs"></a>Criar várias linhas de guias  
  
1.  Adicione o número de páginas de guia desejado.  
  
2.  Defina as <xref:System.Windows.Forms.TabControl.Multiline%2A> propriedade do <xref:System.Windows.Forms.TabControl> para `true`.  
  
3.  Se as guias não aparecem em várias linhas, defina as <xref:System.Windows.Forms.Control.Width%2A> propriedade do <xref:System.Windows.Forms.TabControl> para ser mais estreita que todas as guias.  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>Organizar as guias na lateral do controle  
  
-   Defina as <xref:System.Windows.Forms.TabControl.Alignment%2A> propriedade do <xref:System.Windows.Forms.TabControl> para <xref:System.Windows.Forms.TabAlignment.Left> ou <xref:System.Windows.Forms.TabAlignment.Right>.  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>Habilitar ou desabilitar todos os controles em uma guia usando programação  
  
1.  Defina as <xref:System.Windows.Forms.TabPage.Enabled%2A> propriedade do <xref:System.Windows.Forms.TabPage> para `true` ou `false`.  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a>Exibir guias como botões  
  
-   Defina as <xref:System.Windows.Forms.TabControl.Appearance%2A> propriedade do <xref:System.Windows.Forms.TabControl> para <xref:System.Windows.Forms.TabAppearance.Buttons> ou <xref:System.Windows.Forms.TabAppearance.FlatButtons>.  
  
## <a name="see-also"></a>Consulte também
- [Controle TabControl](tabcontrol-control-windows-forms.md)
- [Visão geral do controle TabControl](tabcontrol-control-overview-windows-forms.md)
- [Como: Adicionar um controle a uma página da guia](how-to-add-a-control-to-a-tab-page.md)
- [Como: Desabilitar páginas de guia](how-to-disable-tab-pages.md)
- [Como: Adicionar e remover guias com o TabControl dos Windows Forms](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
