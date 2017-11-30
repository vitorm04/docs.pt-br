---
title: "Como alterar a aparência do TabControl dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b244930f0837d3b1d548e0f7a8c77dd80e1ce039
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>Como alterar a aparência do TabControl dos Windows Forms
Você pode alterar a aparência das guias em formulários do Windows usando as propriedades do <xref:System.Windows.Forms.TabControl> e <xref:System.Windows.Forms.TabPage> objetos que compõem as guias individuais no controle. Ao configurar essas propriedades, é possível exibir imagens em guias, exibir guias verticalmente em vez de horizontalmente, exibir várias linhas de guias e habilitar ou desabilitar guias com programação.  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>Exibir um ícone na parte de rótulo de uma guia  
  
1.  Adicionar um <xref:System.Windows.Forms.ImageList> controle no formulário.  
  
2.  Adicione imagens à lista de imagens.  
  
     Para obter mais informações sobre listas de imagens, consulte [Componente ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) e [Como adicionar ou remover imagens com o componente ImageList dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
3.  Definir o <xref:System.Windows.Forms.TabControl.ImageList%2A> propriedade o <xref:System.Windows.Forms.TabControl> para o <xref:System.Windows.Forms.ImageList> controle.  
  
4.  Definir o <xref:System.Windows.Forms.TabPage.ImageIndex%2A> propriedade o <xref:System.Windows.Forms.TabPage> para o índice de uma imagem apropriada na lista.  
  
### <a name="to-create-multiple-rows-of-tabs"></a>Criar várias linhas de guias  
  
1.  Adicione o número de páginas de guia desejado.  
  
2.  Definir o <xref:System.Windows.Forms.TabControl.Multiline%2A> propriedade o <xref:System.Windows.Forms.TabControl> para `true`.  
  
3.  Se as guias não aparecem em várias linhas, definir o <xref:System.Windows.Forms.Control.Width%2A> propriedade o <xref:System.Windows.Forms.TabControl> para ser mais estreitas do que todas as guias.  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>Organizar as guias na lateral do controle  
  
-   Definir o <xref:System.Windows.Forms.TabControl.Alignment%2A> propriedade o <xref:System.Windows.Forms.TabControl> para <xref:System.Windows.Forms.TabAlignment.Left> ou <xref:System.Windows.Forms.TabAlignment.Right>.  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>Habilitar ou desabilitar todos os controles em uma guia usando programação  
  
1.  Definir o <xref:System.Windows.Forms.TabPage.Enabled%2A> propriedade o <xref:System.Windows.Forms.TabPage> para `true` ou `false`.  
  
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
  
-   Definir o <xref:System.Windows.Forms.TabControl.Appearance%2A> propriedade o <xref:System.Windows.Forms.TabControl> para <xref:System.Windows.Forms.TabAppearance.Buttons> ou <xref:System.Windows.Forms.TabAppearance.FlatButtons>.  
  
## <a name="see-also"></a>Consulte também  
 [Controle TabControl](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [Visão geral do controle TabControl](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [Como adicionar um controle a uma página da guia](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [Como desabilitar páginas de guia](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [Como adicionar e remover guias com o TabControl dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
