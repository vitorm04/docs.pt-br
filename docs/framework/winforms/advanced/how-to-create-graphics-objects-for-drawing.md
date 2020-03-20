---
title: Como criar objetos gráficos para desenho
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
ms.openlocfilehash: d591d65904484e33285e5db7aa99760f3e1909d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142427"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>Como criar objetos gráficos para desenho
Antes de desenhar linhas e formas, renderizar texto ou exibir e manipular <xref:System.Drawing.Graphics> imagens com GDI+, você precisa criar um objeto. O <xref:System.Drawing.Graphics> objeto representa uma superfície de desenho GDI+, e é o objeto que é usado para criar imagens gráficas.  
  
 Há duas etapas ao trabalhar com gráficos:  
  
1. Criando <xref:System.Drawing.Graphics> um objeto.  
  
2. Usando <xref:System.Drawing.Graphics> o objeto para desenhar linhas e formas, renderizar texto ou exibir e manipular imagens.  
  
## <a name="creating-a-graphics-object"></a>Criando um objeto gráfico  
 Um objeto gráfico pode ser criado de várias maneiras.  
  
#### <a name="to-create-a-graphics-object"></a>Para criar um objeto gráfico  
  
- Receba uma referência a um objeto <xref:System.Windows.Forms.PaintEventArgs> gráfico <xref:System.Windows.Forms.Control.Paint> como parte do caso de um formulário ou controle. Geralmente é assim que você obtém uma referência a um objeto gráfico ao criar código de pintura para um controle. Da mesma forma, você também pode obter <xref:System.Drawing.Printing.PrintPageEventArgs> um objeto <xref:System.Drawing.Printing.PrintDocument.PrintPage> gráfico como <xref:System.Drawing.Printing.PrintDocument>propriedade do ao manipular o evento para um .  
  
     -ou-  
  
- Chame <xref:System.Windows.Forms.Control.CreateGraphics%2A> o método de um controle ou <xref:System.Drawing.Graphics> formulário para obter uma referência a um objeto que representa a superfície de desenho desse controle ou forma. Use esse método se quiser desenhar em um formulário ou controle que já exista.  
  
     -ou-  
  
- Crie <xref:System.Drawing.Graphics> um objeto a partir <xref:System.Drawing.Image>de qualquer objeto que herde . Essa abordagem é útil quando você quer alterar uma imagem existente.  
  
     As seções a seguir dão detalhes sobre cada um desses processos.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>PaintEventArgs no manipulador de eventos de pintura  
 Ao programar <xref:System.Windows.Forms.PaintEventHandler> os controles <xref:System.Drawing.Printing.PrintDocument.PrintPage> ou <xref:System.Drawing.Printing.PrintDocument>para um , um objeto gráfico é <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs>fornecido como uma das propriedades de ou .  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Para obter uma referência a um objeto Gráfico de PaintEventArgs no evento de pintura  
  
1. Declare <xref:System.Drawing.Graphics> o objeto.  
  
2. Atribuir a variável para <xref:System.Drawing.Graphics> se referir ao <xref:System.Windows.Forms.PaintEventArgs>objeto passado como parte do .  
  
3. Inserir código para pintar o formulário ou o controle.  
  
     O exemplo a seguir <xref:System.Drawing.Graphics> mostra como <xref:System.Windows.Forms.PaintEventArgs> referenciar um objeto do <xref:System.Windows.Forms.Control.Paint> evento:  
  
    ```vb  
    Private Sub Form1_Paint(sender As Object, pe As PaintEventArgs) Handles _  
       MyBase.Paint  
       ' Declares the Graphics object and sets it to the Graphics object  
       ' supplied in the PaintEventArgs.  
       Dim g As Graphics = pe.Graphics  
       ' Insert code to paint the form here.  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Paint(object sender,
       System.Windows.Forms.PaintEventArgs pe)
    {  
       // Declares the Graphics object and sets it to the Graphics object  
       // supplied in the PaintEventArgs.  
       Graphics g = pe.Graphics;  
       // Insert code to paint the form here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void Form1_Paint(System::Object ^ sender,  
          System::Windows::Forms::PaintEventArgs ^ pe)  
       {  
          // Declares the Graphics object and sets it to the Graphics object  
          // supplied in the PaintEventArgs.  
          Graphics ^ g = pe->Graphics;  
          // Insert code to paint the form here.  
       }  
    ```  
  
## <a name="creategraphics-method"></a>Método CreateGraphics  
 Você também pode <xref:System.Windows.Forms.Control.CreateGraphics%2A> usar o método de um controle <xref:System.Drawing.Graphics> ou formulário para obter uma referência a um objeto que representa a superfície de desenho desse controle ou forma.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>Para criar um objeto gráfico com o método CreateGraphics  
  
- Chame <xref:System.Windows.Forms.Control.CreateGraphics%2A> o método do formulário ou controle sobre o qual você deseja renderizar gráficos.  
  
    ```vb  
    Dim g as Graphics  
    ' Sets g to a Graphics object representing the drawing surface of the  
    ' control or form g is a member of.  
    g = Me.CreateGraphics  
    ```  
  
    ```csharp  
    Graphics g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this.CreateGraphics();  
    ```  
  
    ```cpp  
    Graphics ^ g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this->CreateGraphics();  
    ```  
  
## <a name="create-from-an-image-object"></a>Criar de um objeto de imagem  
 Além disso, você pode criar um objeto gráfico <xref:System.Drawing.Image> a partir de qualquer objeto que deriva da classe.  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Para criar um objeto Gráfico de uma imagem  
  
- Ligue <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> para o método, fornecendo o nome da variável <xref:System.Drawing.Graphics> Imagem a partir da qual você deseja criar um objeto.  
  
     O exemplo a seguir <xref:System.Drawing.Bitmap> mostra como usar um objeto:  
  
    ```vb  
    Dim myBitmap as New Bitmap("C:\Documents and Settings\Joe\Pics\myPic.bmp")  
    Dim g as Graphics = Graphics.FromImage(myBitmap)  
    ```  
  
    ```csharp  
    Bitmap myBitmap = new Bitmap(@"C:\Documents and
       Settings\Joe\Pics\myPic.bmp");  
    Graphics g = Graphics.FromImage(myBitmap);  
    ```  
  
    ```cpp  
    Bitmap ^ myBitmap = gcnew  
       Bitmap("D:\\Documents and Settings\\Joe\\Pics\\myPic.bmp");  
    Graphics ^ g = Graphics::FromImage(myBitmap);  
    ```  
  
> [!NOTE]
> Você só <xref:System.Drawing.Graphics> pode criar objetos a partir de arquivos .bmp não indexados, como arquivos de 16 bits, 24 bits e 32 bits .bmp. Cada pixel dos arquivos .bmp não indexados mantém uma cor, em contraste com pixels de arquivos .bmp indexados, que mantêm um índice para uma tabela de cores.  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Desenhar e manipular imagens e formas  
 Depois de criado, <xref:System.Drawing.Graphics> um objeto pode ser usado para desenhar linhas e formas, renderizar texto ou exibir e manipular imagens. Os principais objetos <xref:System.Drawing.Graphics> usados com o objeto são:  
  
- A <xref:System.Drawing.Pen> classe — usada para desenhar linhas, delinear formas ou renderizar outras representações geométricas.  
  
- A <xref:System.Drawing.Brush> classe — usada para preencher áreas de gráficos, como formas preenchidas, imagens ou texto.  
  
- A <xref:System.Drawing.Font> classe — fornece uma descrição de quais formas usar ao renderizar texto.  
  
- A <xref:System.Drawing.Color> estrutura representa as diferentes cores a serem exibidas.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Para usar o objeto Gráfico que você criou  
  
- Trabalhe com o objeto apropriado listado acima para desenhar o que você precisa.  
  
     Para obter mais informações, consulte estes tópicos:  
  
    |Para renderizar|Consulte|  
    |---------------|---------|  
    |Linhas|[Como desenhar uma linha em um formulário do Windows Forms](how-to-draw-a-line-on-a-windows-form.md)|  
    |Formas|[Como desenhar uma forma delineada](how-to-draw-an-outlined-shape.md)|  
    |Texto|[Como desenhar texto em um formulário do Windows Forms](how-to-draw-text-on-a-windows-form.md)|  
    |Imagens|[Como renderizar imagens com o GDI+](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>Confira também

- [Introdução à Programação de Elementos Gráficos](getting-started-with-graphics-programming.md)
- [Elementos gráficos e desenho no Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Linhas, curvas e formas](lines-curves-and-shapes.md)
- [Como renderizar imagens com o GDI+](how-to-render-images-with-gdi.md)
