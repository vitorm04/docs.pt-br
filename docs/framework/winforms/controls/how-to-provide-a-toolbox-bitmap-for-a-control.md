---
title: Como fornecer um bitmap da caixa de ferramentas para um controle
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d34cbb88805d9c034df61aba89ebd7bb224b1da
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>Como fornecer um bitmap da caixa de ferramentas para um controle
Se você deseja ter um ícone especial para o seu controle aparecem no **caixa de ferramentas**, você pode especificar uma imagem específica usando o <xref:System.Drawing.ToolboxBitmapAttribute>. Esta classe é um *atributo*, um tipo especial de classe que você pode anexar a outras classes. Para obter mais informações sobre atributos, consulte [não está em compilação: Visão geral de atributos no Visual Basic](http://msdn.microsoft.com/library/0d0cff64-892d-4f57-83bd-bef388553d4f) do Visual Basic e [atributos](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205) para Visual c#.  
  
 Usando o <xref:System.Drawing.ToolboxBitmapAttribute>, você pode especificar uma cadeia de caracteres que indica o caminho e nome de arquivo para um bitmap de 16 por 16 pixels. O bitmap aparece ao lado de seu controle quando adicionado à **Caixa de ferramentas**. Você também pode especificar um <xref:System.Type>, caso em que o bitmap associado com o tipo é carregado. Se você especificar ambos um <xref:System.Type> e uma cadeia de caracteres, o controle de pesquisa para um recurso de imagem com o nome especificado pelo parâmetro de cadeia de caracteres no assembly que contém o tipo especificado pelo <xref:System.Type> parâmetro.  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>Especificar um bitmap da caixa de ferramentas para seu controle  
  
1.  Adicionar o <xref:System.Drawing.ToolboxBitmapAttribute> à declaração de classe do controle antes do `Class` palavra-chave do visual Basic e acima da declaração de classe para o Visual c#.  
  
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
    >  O bitmap não aparece na caixa de ferramentas para controles e componentes gerados automaticamente. Para ver o bitmap, recarregue o controle usando a caixa de diálogo **Escolher Itens da Caixa de Ferramentas**. Para mais informações, consulte [Instruções passo a passo: preenchendo de forma automática a caixa de ferramentas com componentes personalizados](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.ToolboxBitmapAttribute>  
 [Passo a passo: preenchendo automaticamente a caixa de ferramentas com componentes personalizados](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [Desenvolvendo controles dos Windows Forms em tempo de design](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Atributos (Visual Basic)](~/docs/visual-basic/language-reference/attributes.md)  
 [Atributos](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
