---
title: 'Como: Criar chaves de acesso para controles do Windows Forms'
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
ms.openlocfilehash: ccec8bba9e01cbaa7bfef841af68a0fcaa720b90
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658373"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a>Como: Criar chaves de acesso para controles de Windows Forms

Uma *chave de acesso* é um caractere de sublinhado no texto de um menu, item de menu ou rótulo de um controle como um botão. Com uma chave de acesso, o usuário pode "clicar" em um botão pressionando a tecla Alt em combinação com a chave de acesso predefinida. Por exemplo, se um botão executar um procedimento para imprimir um formulário e, portanto, `Text` sua propriedade estiver definida como "imprimir", adicionar um e comercial antes da letra "p" fará com que a letra "p" seja sublinhada no texto do botão em tempo de execução. O usuário pode executar o comando associado ao botão pressionando ALT + P.

Controles que não podem receber foco não podem ter chaves de acesso.

## <a name="programmatic"></a>Program

Defina a `Text` Propriedade como uma cadeia de caracteres que inclui um e comercial (&) antes da letra que será o atalho.

```vb
' Set the letter "P" as an access key.
Button1.Text = "&Print"
```

```csharp
// Set the letter "P" as an access key.
button1.Text = "&Print";
```

```cpp
// Set the letter "P" as an access key.
button1->Text = "&Print";
```

> [!NOTE]
> Para usar um e comercial em uma legenda sem criar uma chave de acesso, inclua dois e comercial (& &). Um único e comercial é exibido na legenda e nenhum caractere é sublinhado.

## <a name="designer"></a>Designer

Na janela **Propriedades** do Visual Studio, defina a propriedade **Text** como uma cadeia de caracteres que inclua um e comercial (' & ') antes da letra que será a chave de acesso. Por exemplo, para definir a letra "P" como a chave de acesso, insira **& imprimir**.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Button>
- [Como: Responder a Windows Forms cliques de botão](how-to-respond-to-windows-forms-button-clicks.md)
- [Como: Definir o texto exibido por um controle de Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
