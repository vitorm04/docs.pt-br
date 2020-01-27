---
title: Alterar a aparência do TabControl
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
ms.openlocfilehash: 056070177e6bbaba0c93c7b94f5adfd7887be6a8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746618"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>Como alterar a aparência do TabControl dos Windows Forms
Você pode alterar a aparência das guias em Windows Forms usando as propriedades do <xref:System.Windows.Forms.TabControl> e os objetos <xref:System.Windows.Forms.TabPage> que compõem as guias individuais do controle. Ao configurar essas propriedades, é possível exibir imagens em guias, exibir guias verticalmente em vez de horizontalmente, exibir várias linhas de guias e habilitar ou desabilitar guias com programação.  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>Exibir um ícone na parte de rótulo de uma guia  
  
1. Adicione um controle de <xref:System.Windows.Forms.ImageList> ao formulário.  
  
2. Adicione imagens à lista de imagens.  
  
     Para obter mais informações sobre listas de imagens, consulte [Componente ImageList](imagelist-component-windows-forms.md) e [Como adicionar ou remover imagens com o componente ImageList dos Windows Forms](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
3. Defina a propriedade <xref:System.Windows.Forms.TabControl.ImageList%2A> do <xref:System.Windows.Forms.TabControl> para o controle de <xref:System.Windows.Forms.ImageList>.  
  
4. Defina a propriedade <xref:System.Windows.Forms.TabPage.ImageIndex%2A> do <xref:System.Windows.Forms.TabPage> como o índice de uma imagem apropriada na lista.  
  
### <a name="to-create-multiple-rows-of-tabs"></a>Criar várias linhas de guias  
  
1. Adicione o número de páginas de guia desejado.  
  
2. Defina a propriedade <xref:System.Windows.Forms.TabControl.Multiline%2A> da <xref:System.Windows.Forms.TabControl> como `true`.  
  
3. Se as guias ainda não aparecerem em várias linhas, defina a propriedade <xref:System.Windows.Forms.Control.Width%2A> da <xref:System.Windows.Forms.TabControl> como mais estreita do que todas as guias.  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>Organizar as guias na lateral do controle  
  
- Defina a propriedade <xref:System.Windows.Forms.TabControl.Alignment%2A> da <xref:System.Windows.Forms.TabControl> como <xref:System.Windows.Forms.TabAlignment.Left> ou <xref:System.Windows.Forms.TabAlignment.Right>.  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>Habilitar ou desabilitar todos os controles em uma guia usando programação  
  
1. Defina a propriedade <xref:System.Windows.Forms.TabPage.Enabled%2A> da <xref:System.Windows.Forms.TabPage> como `true` ou `false`.  
  
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
  
- Defina a propriedade <xref:System.Windows.Forms.TabControl.Appearance%2A> da <xref:System.Windows.Forms.TabControl> como <xref:System.Windows.Forms.TabAppearance.Buttons> ou <xref:System.Windows.Forms.TabAppearance.FlatButtons>.  
  
## <a name="see-also"></a>Veja também

- [Controle TabControl](tabcontrol-control-windows-forms.md)
- [Visão geral do controle TabControl](tabcontrol-control-overview-windows-forms.md)
- [Como adicionar um controle a uma página da guia](how-to-add-a-control-to-a-tab-page.md)
- [Como desabilitar páginas de guia](how-to-disable-tab-pages.md)
- [Como adicionar e remover guias com o TabControl dos Windows Forms](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
