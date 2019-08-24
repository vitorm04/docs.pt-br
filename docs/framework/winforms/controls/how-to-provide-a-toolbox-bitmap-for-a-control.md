---
title: 'Como: Fornecer um bitmap da caixa de ferramentas para um controle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e6da7318ba481af721a9220c8f71af2a18e764a3
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015785"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>Como: Fornecer um bitmap da caixa de ferramentas para um controle

Se você quiser ter um ícone especial para seu controle aparecer na caixa de **ferramentas** do Visual Studio, poderá especificar uma imagem específica usando o <xref:System.Drawing.ToolboxBitmapAttribute>. Esta classe é um *atributo*, um tipo especial de classe que você pode anexar a outras classes. Para obter mais informações sobre atributos, consulte [visão geral de atributos (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) para Visual Basic ou [atributos (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) para. C#

Usando o <xref:System.Drawing.ToolboxBitmapAttribute>, você pode especificar uma cadeia de caracteres que indica o caminho e o nome do arquivo para um bitmap de 16 por 16 pixels. O bitmap aparece ao lado de seu controle quando adicionado à **Caixa de ferramentas**. Você também pode especificar um <xref:System.Type>, caso em que o bitmap associado a esse tipo é carregado. Se você especificar um <xref:System.Type> e uma cadeia de caracteres, o controle pesquisará um recurso de imagem com o nome especificado pelo parâmetro de cadeia de caracteres no assembly que contém o tipo especificado <xref:System.Type> pelo parâmetro.

## <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>Especificar um bitmap da caixa de ferramentas para seu controle

1. Adicione o <xref:System.Drawing.ToolboxBitmapAttribute> à declaração de classe do seu controle antes da `Class` palavra-chave para Visual Basic e acima da declaração de classe C#para Visual.

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

2. Recompile o projeto.

    > [!NOTE]
    > O bitmap não aparece na caixa de ferramentas para controles e componentes gerados automaticamente. Para ver o bitmap, recarregue o controle usando a caixa de diálogo **Escolher Itens da Caixa de Ferramentas**. Para obter mais informações, confira [Passo a passo: Populando automaticamente a caixa de](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)ferramentas com componentes personalizados.

## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [Passo a passo: Populando automaticamente a caixa de ferramentas com componentes personalizados](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Desenvolvendo controles dos Windows Forms em tempo de design](developing-windows-forms-controls-at-design-time.md)
- [Visão geral de atributos (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Atributos (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)
