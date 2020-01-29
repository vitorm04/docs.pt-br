---
title: Como modificar o tamanho ou a colocação de uma imagem em tempo de execução
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
ms.openlocfilehash: 9bb094ce0b7945f23a2e9b8614e56c9492d5f832
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736031"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>Como modificar o tamanho ou a colocação de uma imagem em tempo de execução (Windows Forms)
Se você usar o controle de <xref:System.Windows.Forms.PictureBox> Windows Forms em um formulário, poderá definir a propriedade <xref:System.Windows.Forms.PictureBox.SizeMode%2A> para:  
  
- Alinhe o canto superior esquerdo da imagem com o canto superior esquerdo do controle  
  
- Centralize a imagem no controle  
  
- Ajuste o tamanho do controle para se adaptar à imagem exibida  
  
- Alongue qualquer imagem exibida para se ajustar ao controle  
  
 Ampliar uma imagem (especialmente em formato bitmap) pode causar perda na qualidade. Metarquivos, que são listas de instruções gráficas para desenho de imagens em tempo de execução, são mais adequados para ampliar do que os bitmaps.  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>Para definir a propriedade SizeMode em tempo de execução  
  
1. Defina <xref:System.Windows.Forms.PictureBox.SizeMode%2A> como <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (o padrão), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>ou <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>. <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> significa que a imagem é colocada no canto superior esquerdo do controle; se a imagem for maior do que o controle, suas bordas inferior e direita serão recortadas. <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> significa que a imagem está centralizada dentro do controle; se a imagem for maior que o controle, as bordas externas da imagem serão recortadas. <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> significa que o tamanho do controle é ajustado para o tamanho da imagem. <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> é o inverso e significa que o tamanho da imagem é ajustado para o tamanho do controle.  
  
     No exemplo abaixo, o caminho definido para o local da imagem é a pasta Meus Documentos. Isso acontece porque presumimos que a maioria dos computadores rodando o sistema operacional Windows vai incluir este diretório. Isso também permite que usuários com níveis mínimos de acesso ao sistema executem com segurança o aplicativo. O exemplo a seguir pressupõe um formulário com um controle de <xref:System.Windows.Forms.PictureBox> já adicionado.  
  
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
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.PictureBox>
- [Como carregar uma imagem usando o designer](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [Visão geral do controle PictureBox](picturebox-control-overview-windows-forms.md)
- [Como definir imagens em tempo de execução](how-to-set-pictures-at-run-time-windows-forms.md)
- [Controle PictureBox](picturebox-control-windows-forms.md)
