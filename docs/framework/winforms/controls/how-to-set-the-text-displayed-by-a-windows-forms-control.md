---
title: 'Como: Definir o texto exibido por um controle do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: e9bf2077f10648dbe3ebf214bbbf9546cbb398c3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096180"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>Como: Definir o texto exibido por um controle do Windows Forms
Controles dos Windows Forms normalmente exibem algum texto que está relacionado à função primária do controle. Por exemplo, um <xref:System.Windows.Forms.Button> controle normalmente exibe uma legenda que indica qual ação será executada quando o botão é clicado. Para todos os controles, você pode definir ou retornar o texto usando o <xref:System.Windows.Forms.Control.Text%2A> propriedade. Você pode alterar a fonte usando o <xref:System.Windows.Forms.Control.Font%2A> propriedade. Você também pode definir o texto usando o designer.  Consulte também [como: Criar chaves de acesso para controles usando o Designer de formulários do Windows](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md), [como: Definir o texto exibido por um Windows Forms usando o Designer de controle](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md), [como: Definir a imagem exibida por um Windows Forms usando o Designer de controle](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md).  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a>Como definir o texto exibido por um controle de forma programática  
  
1.  Defina o <xref:System.Windows.Forms.Control.Text%2A> propriedade como uma cadeia de caracteres.  
  
     Para criar uma tecla de acesso sublinhada, inclua um e comercial (&) antes da letra que será a tecla de acesso.  
  
2.  Defina as <xref:System.Windows.Forms.Control.Font%2A> propriedade para um objeto do tipo <xref:System.Drawing.Font>.  
  
    ```vb  
    Button1.Text = "Click here to save changes"  
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)  
    ```  
  
    ```csharp  
    button1.Text = "Click here to save changes";  
    button1.Font = new Font("Arial", 10, FontStyle.Bold,  
       GraphicsUnit.Point);  
    ```  
  
    ```cpp  
    button1->Text = "Click here to save changes";  
    button1->Font = new System::Drawing::Font("Arial",  
       10, FontStyle::Bold, GraphicsUnit::Point);  
    ```  
  
    > [!NOTE]
    >  Você pode usar um caractere de escape para exibir um caractere especial nos elementos de interface do usuário que seriam normalmente interpretados de maneira diferente, como itens de menu. Por exemplo, a linha de código a seguir define o texto do item de menu para ler "& agora para algo completamente diferente":  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
    ```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [Como: Criar chaves de acesso para controles do Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md)
- [Como: Responder a cliques no botão do Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
