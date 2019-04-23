---
title: 'Como: Definir imagens em tempo de execução (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
ms.openlocfilehash: 8ed3ba9050a9117a53b5f4f1cccd26381f55ab32
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073592"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>Como: Definir imagens em tempo de execução (Windows Forms)
Você pode definir programaticamente a imagem exibida por um Windows Forms <xref:System.Windows.Forms.PictureBox> controle.  
  
### <a name="to-set-a-picture-programmatically"></a>Para definir uma imagem de forma programática  
  
-   Definir o <xref:System.Windows.Forms.PictureBox.Image%2A> propriedade usando o <xref:System.Drawing.Image.FromFile%2A> método o <xref:System.Drawing.Image> classe.  
  
     No exemplo abaixo, o caminho definido para o local da imagem é a pasta Meus Documentos. Isso acontece porque presumimos que a maioria dos computadores rodando o sistema operacional Windows vai incluir este diretório. Isso também permite que usuários com níveis mínimos de acesso ao sistema executem com segurança o aplicativo. O exemplo a seguir supõe um formulário com um <xref:System.Windows.Forms.PictureBox> controle já adicionado.  
  
    ```vb  
    Private Sub LoadNewPict()  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadNewPict(){  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    }  
    ```  
  
    ```cpp  
    private:  
       void LoadNewPict()  
       {  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
### <a name="to-clear-a-graphic"></a>Para desmarcar um elemento gráfico  
  
-   Primeiro, liberar a memória que está sendo usada pela imagem e, em seguida, desmarque o elemento gráfico. Coleta de lixo liberará a memória mais tarde se o gerenciamento de memória se torna um problema.  
  
    ```vb  
    If Not (PictureBox1.Image Is Nothing) Then  
       PictureBox1.Image.Dispose()  
       PictureBox1.Image = Nothing  
    End If  
    ```  
  
    ```csharp  
    if (pictureBox1.Image != null)   
    {  
       pictureBox1.Image.Dispose();  
       pictureBox1.Image = null;  
    }  
    ```  
  
    ```cpp  
    if (pictureBox1->Image != nullptr)  
    {  
       pictureBox1->Image->Dispose();  
       pictureBox1->Image = nullptr;  
    }  
    ```  
  
    > [!NOTE]
    >  Para obter mais informações sobre por que você deve usar o <xref:System.Drawing.Image.Dispose%2A> método dessa forma, consulte [limpeza de recursos não gerenciados](../../../standard/garbage-collection/unmanaged.md).  
  
     Esse código limpará a imagem, mesmo se um elemento gráfico foi carregado no controle em tempo de design.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [Visão geral do controle PictureBox](picturebox-control-overview-windows-forms.md)
- [Como: Carregar uma imagem usando o Designer](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [Como: Modificar o tamanho ou a colocação de uma imagem em tempo de execução](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Controle PictureBox](picturebox-control-windows-forms.md)
