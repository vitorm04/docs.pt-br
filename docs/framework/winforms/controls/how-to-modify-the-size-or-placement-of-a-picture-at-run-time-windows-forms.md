---
title: 'Como: Modificar o tamanho ou a colocação de uma imagem em tempo de execução (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], controlling placement in PictureBox control [Windows Forms]
- examples [Windows Forms], PictureBox control
- PictureBox control [Windows Forms], picture size and alignment
- pictures [Windows Forms], controlling placement in PictureBox control [Windows Forms]
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
ms.openlocfilehash: 695abf51870ef9164e4543a91b3183e801eee55f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649250"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>Como: Modificar o tamanho ou a colocação de uma imagem em tempo de execução (Windows Forms)
Se você usar o Windows Forms <xref:System.Windows.Forms.PictureBox> controle em um formulário, você pode definir o <xref:System.Windows.Forms.PictureBox.SizeMode%2A> propriedade nele para:  
  
- Alinhe o canto superior esquerdo da imagem com o canto superior esquerdo do controle  
  
- Centralize a imagem no controle  
  
- Ajuste o tamanho do controle para se adaptar à imagem exibida  
  
- Alongue qualquer imagem exibida para se ajustar ao controle  
  
 Ampliar uma imagem (especialmente em formato bitmap) pode causar perda na qualidade. Metarquivos, que são listas de instruções gráficas para desenho de imagens em tempo de execução, são mais adequados para ampliar do que os bitmaps.  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>Para definir a propriedade SizeMode em tempo de execução  
  
1. Definir <xref:System.Windows.Forms.PictureBox.SizeMode%2A> à <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (o padrão), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, ou <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>. <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> significa que a imagem é colocada no canto superior esquerdo do controle; Se a imagem for maior que o controle, suas bordas inferiores e direita serão cortadas. <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> significa que a imagem é centralizada no controle; Se a imagem for maior que o controle, as bordas exteriores serão cortadas. <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> significa que o tamanho do controle é ajustado para o tamanho da imagem. <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> é o inverso e significa que o tamanho da imagem é ajustado para o tamanho do controle.  
  
     No exemplo abaixo, o caminho definido para o local da imagem é a pasta Meus Documentos. Isso acontece porque presumimos que a maioria dos computadores rodando o sistema operacional Windows vai incluir este diretório. Isso também permite que usuários com níveis mínimos de acesso ao sistema executem com segurança o aplicativo. O exemplo a seguir supõe um formulário com um <xref:System.Windows.Forms.PictureBox> controle já adicionado.  
  
    ```vb  
    Private Sub StretchPic()  
       ' Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage  
       ' Load the picture into the control.  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void StretchPic(){  
       // Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;  
       // Load the picture into the control.  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Image.gif")  
    }  
    ```  
  
    ```cpp  
    private:  
       void StretchPic()  
       {  
          // Stretch the picture to fit the control.  
          pictureBox1->SizeMode = PictureBoxSizeMode::StretchImage;  
          // Load the picture into the control.  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.PictureBox>
- [Como: Carregar uma imagem usando o Designer](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [Visão geral do controle PictureBox](picturebox-control-overview-windows-forms.md)
- [Como: Definir imagens em tempo de execução](how-to-set-pictures-at-run-time-windows-forms.md)
- [Controle PictureBox](picturebox-control-windows-forms.md)
