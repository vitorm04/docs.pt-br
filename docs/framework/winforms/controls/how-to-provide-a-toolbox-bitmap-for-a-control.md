---
title: 'Como: Fornecer um Bitmap da caixa de ferramentas para um controle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
ms.openlocfilehash: 9072f96bd6e3485e759ed72819229b3f0c33d641
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715952"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>Como: Fornecer um Bitmap da caixa de ferramentas para um controle
Se você quiser ter um ícone especial para o seu controle apareça na **caixa de ferramentas**, você pode especificar uma imagem específica usando o <xref:System.Drawing.ToolboxBitmapAttribute>. Esta classe é um *atributo*, um tipo especial de classe que você pode anexar a outras classes. Para obter mais informações sobre atributos, consulte [visão geral de atributos (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) para o Visual Basic ou [atributos (c#)](../../../csharp/programming-guide/concepts/attributes/index.md) para c#.  
  
 Usando o <xref:System.Drawing.ToolboxBitmapAttribute>, você pode especificar uma cadeia de caracteres que indica o nome de arquivo e caminho para um bitmap de 16 por 16 pixels. O bitmap aparece ao lado de seu controle quando adicionado à **Caixa de ferramentas**. Você também pode especificar um <xref:System.Type>, caso em que o bitmap associado a esse tipo é carregado. Se você especificar uma <xref:System.Type> e uma cadeia de caracteres, o controle procurará por um recurso de imagem com o nome especificado pelo parâmetro de cadeia de caracteres no assembly que contém o tipo especificado pelo <xref:System.Type> parâmetro.  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>Especificar um bitmap da caixa de ferramentas para seu controle  
  
1.  Adicione a <xref:System.Drawing.ToolboxBitmapAttribute> à declaração de classe do seu controle antes do `Class` palavra-chave para o visual Basic e acima da declaração de classe do Visual c#.  
  
    ```vb  
    ' Specifies the bitmap associated with the Button type.  
    <ToolboxBitmap(GetType(Button))> Class MyControl1  
    ' Specifies a bitmap file.  
    End Class  
    <ToolboxBitmap("C:\Documents and Settings\Joe\MyPics\myImage.bmp")> _  
       Class MyControl2  
    End Class  
    ' Specifies a type that indicates the assembly to search, and the name   
    ' of an image resource to look for.  
    <ToolboxBitmap(GetType(MyControl), "MyControlBitmap")> Class MyControl  
    End Class  
    ```  
  
    ```csharp  
    // Specifies the bitmap associated with the Button type.  
    [ToolboxBitmap(typeof(Button))]  
    class MyControl1 : UserControl  
    {  
    }  
    // Specifies a bitmap file.  
    [ToolboxBitmap(@"C:\Documents and Settings\Joe\MyPics\myImage.bmp")]  
    class MyControl2 : UserControl  
    {  
    }  
    // Specifies a type that indicates the assembly to search, and the name   
    // of an image resource to look for.  
    [ToolboxBitmap(typeof(MyControl), "MyControlBitmap")]  
    class MyControl : UserControl  
    {  
    }  
    ```  
  
2.  Recompile o projeto.  
  
    > [!NOTE]
    >  O bitmap não aparece na caixa de ferramentas para controles e componentes gerados automaticamente. Para ver o bitmap, recarregue o controle usando a caixa de diálogo **Escolher Itens da Caixa de Ferramentas**. Para obter mais informações, confira [Passo a passo: Preenchendo automaticamente a caixa de ferramentas com componentes personalizados](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [Passo a passo: Preenchendo automaticamente a caixa de ferramentas com componentes personalizados](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Desenvolvendo controles dos Windows Forms em tempo de design](developing-windows-forms-controls-at-design-time.md)
- [Visão geral de atributos (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Atributos (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)
