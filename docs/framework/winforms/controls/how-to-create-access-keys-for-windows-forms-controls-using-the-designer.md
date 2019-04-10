---
title: 'Como: Criar teclas de acesso para controles do Windows Forms usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
ms.openlocfilehash: 900a955173c28c7b86fce73e418561ed437719c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216919"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a>Como: Criar teclas de acesso para controles do Windows Forms usando o Designer
Uma *chave de acesso* é um caractere de sublinhado no texto de um menu, item de menu ou rótulo de um controle como um botão. Ela permite que o usuário "clique" em um botão pressionando a tecla ALT em combinação com a chave de acesso predefinida. Por exemplo, se um botão executa um procedimento para imprimir um formulário e, portanto, sua propriedade `Text` estiver definida como "Print", adicionar um e comercial (&) antes da letra "P" faz com que a letra "P" seja sublinhada no texto do botão no tempo de execução. O usuário pode executar o comando associado ao botão pressionando ALT+P. Não é possível ter uma chave de acesso para um controle que não possa receber foco.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-an-access-key-for-a-control"></a>Para criar uma chave de acesso para um controle  
  
1.  Na janela **Propriedades**, defina a propriedade `Text` como uma cadeia de caracteres que inclui um e comercial (&) antes da letra que será a chave de acesso. Por exemplo, para definir a letra "P" como a chave de acesso, digite **&Print** na grade.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Button>
- [Como: Responder a cliques no botão do Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Como: Definir o texto exibido por um controle do Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Identificando controles dos Windows Forms individuais e fornecendo atalhos para eles](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
