---
title: 'Como: Definir o texto exibido por um controle do Windows Forms'
ms.date: 08/20/2019
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
ms.openlocfilehash: 887aa5ec9b97770903cd87459d6df5adc3f7ddf0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666149"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>Como: Definir o texto exibido por um controle de Windows Forms

Os controles de Windows Forms geralmente exibem algum texto relacionado à função principal do controle. Por exemplo, um <xref:System.Windows.Forms.Button> controle geralmente exibe uma legenda indicando qual ação será executada se o botão for clicado. Para todos os controles, você pode definir ou retornar o texto usando a <xref:System.Windows.Forms.Control.Text%2A> propriedade. Você pode alterar a fonte usando a <xref:System.Windows.Forms.Control.Font%2A> propriedade.

Você também pode definir o texto usando o [Designer](#designer).

## <a name="programmatic"></a>Program

1. Defina a <xref:System.Windows.Forms.Control.Text%2A> Propriedade como uma cadeia de caracteres.

   Para criar uma tecla de acesso sublinhada, inclua um e comercial (&) antes da letra que será a tecla de acesso.

2. Defina a <xref:System.Windows.Forms.Control.Font%2A> Propriedade como um objeto do tipo <xref:System.Drawing.Font>.

    ```vb
    Button1.Text = "Click here to save changes"
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)
    ```

    ```csharp
    button1.Text = "Click here to save changes";
    button1.Font = new Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point);
    ```

    ```cpp
    button1->Text = "Click here to save changes";
    button1->Font = new System::Drawing::Font("Arial", 10, FontStyle::Bold, GraphicsUnit::Point);
    ```

    > [!NOTE]
    > Você pode usar um caractere de escape para exibir um caractere especial nos elementos de interface do usuário que seriam normalmente interpretados de maneira diferente, como itens de menu. Por exemplo, a linha de código a seguir define o texto do item de menu para ler "& agora para algo completamente diferente":

    ```vb
    MPMenuItem.Text = "&& Now For Something Completely Different"
    ```

    ```csharp
    mpMenuItem.Text = "&& Now For Something Completely Different";
    ```

    ```cpp
    mpMenuItem->Text = "&& Now For Something Completely Different";
    ```

## <a name="designer"></a>Designer

1. Na janela **Propriedades** no Visual Studio, defina a propriedade **Text** do controle como uma cadeia de caracteres apropriada.

   Para criar uma tecla de atalho sublinhada, inclua um e comercial (&) antes da letra que será a tecla de atalho.

2. Na janela **Propriedades** , selecione o botão de reticências![(botão de reticências (...) na janela Propriedades do](./media/visual-studio-ellipsis-button.png)Visual Studio) ao lado da propriedade **Font** .

   Na caixa de diálogo de fonte padrão, escolha a fonte, o estilo da fonte, o tamanho, efeitos (como riscado ou sublinhado) e o script que você deseja.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [Como: Criar chaves de acesso para controles de Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md)
- [Como: Responder a Windows Forms cliques de botão](how-to-respond-to-windows-forms-button-clicks.md)
