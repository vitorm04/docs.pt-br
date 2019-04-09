---
title: 'Como: Criar chaves de acesso para controles do Windows Forms'
ms.date: 03/30/2017
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
ms.openlocfilehash: fefd322afb938453ec1ea23e8ff6de9f9ae2a851
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141629"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a>Como: Criar chaves de acesso para controles do Windows Forms
Uma *chave de acesso* é um caractere de sublinhado no texto de um menu, item de menu ou rótulo de um controle como um botão. Com uma chave de acesso, o usuário pode "clicar" um botão pressionando a tecla ALT em combinação com a chave de acesso predefinidas. Por exemplo, se um botão executa um procedimento para imprimir um formulário e, portanto, seu `Text` estiver definida como "Print", adicionando um e comercial antes que a letra "P" faz com que a letra "P" seja sublinhada no texto do botão no tempo de execução. O usuário pode executar o comando associado ao botão pressionando ALT+P. Não é possível ter uma chave de acesso para um controle que não possa receber foco.  
  
### <a name="to-create-an-access-key-for-a-control"></a>Para criar uma chave de acesso para um controle  
  
1.  Defina o `Text` propriedade como uma cadeia de caracteres que inclua um e comercial (&) antes da letra que será o atalho.  
  
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
    >  Para incluir um e comercial em uma legenda sem criar uma chave de acesso, inclua duas "e" comercial (& &). Um único e comercial é exibido na legenda e caracteres não é sublinhado.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Button>
- [Como: Responder a cliques no botão do Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Como: Definir o texto exibido por um controle do Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Identificando controles dos Windows Forms individuais e fornecendo atalhos para eles](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
