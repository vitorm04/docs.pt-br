---
title: Definir a imagem exibida por um controle
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 5df0068c8462bbaab0cb0135de1dd1b91ababe06
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746878"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>Como definir a imagem exibida por um controle de Windows Forms

Vários controles de Windows Forms podem exibir imagens. Essas imagens podem ser ícones que esclarecem a finalidade do controle, como um ícone de disquete em um botão que indica o comando salvar. Como alternativa, os ícones podem ser imagens de plano de fundo para dar ao controle a aparência e o comportamento que você deseja.

## <a name="programmatic"></a>Programático

Defina a propriedade `Image` ou `BackgroundImage` do controle como um objeto do tipo <xref:System.Drawing.Image>. Em geral, você carregará a imagem de um arquivo usando o método <xref:System.Drawing.Image.FromFile%2A>.

No exemplo de código a seguir, o caminho definido para o local da imagem é a pasta **minhas imagens** . A maioria dos computadores que executam o sistema operacional Windows inclui esse diretório. Isso também permite que os usuários com níveis mínimos de acesso do sistema executem o aplicativo com segurança. O exemplo de código a seguir requer que você já tenha um formulário com um controle de <xref:System.Windows.Forms.PictureBox> adicionado.

```vb
' Replace the image named below with your own icon.
PictureBox1.Image = Image.FromFile _
   (System.Environment.GetFolderPath _
   (System.Environment.SpecialFolder.MyPictures) _
   & "\Image.gif")
```

```csharp
// Replace the image named below with your own icon.
// Note the escape character used (@) when specifying the path.
pictureBox1.Image = Image.FromFile
   (System.Environment.GetFolderPath
   (System.Environment.SpecialFolder.MyPictures)
   + @"\Image.gif");
```

```cpp
// Replace the image named below with your own icon.
pictureBox1->Image = Image::FromFile(String::Concat
   (System::Environment::GetFolderPath
   (System::Environment::SpecialFolder::MyPictures),
   "\\Image.gif"));
```

## <a name="designer"></a>Designer

1. Na janela **Propriedades** do Visual Studio, selecione a propriedade **Image** ou **BackgroundImage** do controle e, em seguida, selecione as reticências (![botão de reticências no Visual Studio](./media/visual-studio-ellipsis-button.png)) para exibir a caixa de diálogo **selecionar recurso** .

2. Selecione a imagem que você deseja exibir.

## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
