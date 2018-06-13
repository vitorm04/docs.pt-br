---
title: Renderizando um controle dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- OnPaintBackground method [Windows Forms], invoking in Windows Forms custom controls
- custom controls [Windows Forms], graphics resources
- custom controls [Windows Forms], invalidation and painting
ms.assetid: aae8e1e6-4786-432b-a15e-f4c44760d302
ms.openlocfilehash: a2d7a02e725e3f8065b80a6b30ea21158be43ea8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541382"
---
# <a name="rendering-a-windows-forms-control"></a>Renderizando um controle dos Windows Forms
Renderização se refere ao processo de criar uma representação visual na tela do usuário. O Windows Forms usa [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] (a nova biblioteca de gráficos do Windows) para renderização. As classes gerenciadas que fornecem acesso a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] estão no <xref:System.Drawing?displayProperty=nameWithType> namespace e seus subnamespaces.  
  
 Os elementos a seguir estão envolvidos na renderização de controles:  
  
-   A funcionalidade de desenho fornecida pela classe base <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
-   Os elementos essenciais da biblioteca de gráficos [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
-   A geometria da região de desenho.  
  
-   O procedimento para liberar recursos gráficos.  
  
## <a name="drawing-functionality-provided-by-control"></a>Funcionalidade de desenho fornecida pelo controle  
 A classe base <xref:System.Windows.Forms.Control> fornece a funcionalidade de desenho por meio de seu <xref:System.Windows.Forms.Control.Paint> eventos. Um controle gera o <xref:System.Windows.Forms.Control.Paint> evento sempre que precisa atualizar sua exibição. Para obter mais informações sobre os eventos no .NET Framework, consulte [Tratando e gerando eventos](../../../../docs/standard/events/index.md).  
  
 Os dados de eventos de classe para o <xref:System.Windows.Forms.Control.Paint> evento, <xref:System.Windows.Forms.PaintEventArgs>, contém os dados necessários para desenhar um controle — um identificador para um objeto de gráfico e um objeto retângulo que representa a região para desenhar. Esses objetos são mostrados em negrito no seguinte fragmento de código.  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   Implements IDisposable  
  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property  
   ' Other properties and methods.  
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs, IDisposable {  
public System.Drawing.Rectangle ClipRectangle {get;}  
public System.Drawing.Graphics Graphics {get;}  
// Other properties and methods.  
...  
}  
```  
  
 <xref:System.Drawing.Graphics> é uma classe gerenciada que encapsula a funcionalidade de desenho, conforme descrito na discussão de [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] mais adiante neste tópico. O <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> é uma ocorrência da <xref:System.Drawing.Rectangle> estrutura e define a área disponível no qual um controle pode desenhar. Um desenvolvedor de controle pode calcular o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> usando o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriedade de um controle, conforme descrito na discussão de geometria neste tópico.  
  
 Um controle deve fornecer lógica de processamento, substituindo o <xref:System.Windows.Forms.Control.OnPaint%2A> método que ele herda de <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.OnPaint%2A> obtém acesso a um objeto de gráfico e um retângulo para desenhar por meio de <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> e o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriedades da <xref:System.Windows.Forms.PaintEventArgs> instância passada para ele.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 O <xref:System.Windows.Forms.Control.OnPaint%2A> método da base de <xref:System.Windows.Forms.Control> classe não implementa nenhuma funcionalidade de desenho, mas simplesmente chama representantes de eventos que são registrados com o <xref:System.Windows.Forms.Control.Paint> evento. Quando você substituir <xref:System.Windows.Forms.Control.OnPaint%2A>, você normalmente deve chamar o <xref:System.Windows.Forms.Control.OnPaint%2A> método da classe base, de modo que registrado delegados receber o <xref:System.Windows.Forms.Control.Paint> evento. No entanto, os controles de pintura com a superfície inteira não devem chamar a classe base <xref:System.Windows.Forms.Control.OnPaint%2A>, pois isso introduz cintilação. Para obter um exemplo de substituição de <xref:System.Windows.Forms.Control.OnPaint%2A> eventos, consulte o [como: criar um Windows Forms que mostra andamento de controle](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
> [!NOTE]
>  Não invoque <xref:System.Windows.Forms.Control.OnPaint%2A> diretamente no seu controle; em vez disso, invoque o <xref:System.Windows.Forms.Control.Invalidate%2A> método (herdado de <xref:System.Windows.Forms.Control>) ou algum outro método que invoca <xref:System.Windows.Forms.Control.Invalidate%2A>. O <xref:System.Windows.Forms.Control.Invalidate%2A> método por sua vez chama <xref:System.Windows.Forms.Control.OnPaint%2A>. O <xref:System.Windows.Forms.Control.Invalidate%2A> método está sobrecarregado e, dependendo dos argumentos fornecidos para <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, um controle redesenha alguns ou todos os seu área da tela.  
  
 A base de <xref:System.Windows.Forms.Control> classe define outro método que é útil para desenho — o <xref:System.Windows.Forms.Control.OnPaintBackground%2A> método.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> pinta o plano de fundo (e, assim, a forma) da janela e é garantido como sendo rápida, enquanto <xref:System.Windows.Forms.Control.OnPaint%2A> pinta os detalhes e pode ser mais lento porque as solicitações de pintura individuais são combinadas em um <xref:System.Windows.Forms.Control.Paint> evento que abrange todas as áreas que devem ser redesenhado. Talvez você queira invocar o <xref:System.Windows.Forms.Control.OnPaintBackground%2A> se, por exemplo, você deseja desenhar um plano de fundo do gradiente de cores para o seu controle.  
  
 Enquanto <xref:System.Windows.Forms.Control.OnPaintBackground%2A> tem uma evento semelhante a nomenclatura e usa o mesmo argumento, como o `OnPaint` método <xref:System.Windows.Forms.Control.OnPaintBackground%2A> não é um método de evento true. Não há nenhum `PaintBackground` eventos e <xref:System.Windows.Forms.Control.OnPaintBackground%2A> não chama os representantes de eventos. Ao substituir o <xref:System.Windows.Forms.Control.OnPaintBackground%2A> método, uma classe derivada não é necessária para chamar o <xref:System.Windows.Forms.Control.OnPaintBackground%2A> método de sua classe base.  
  
## <a name="gdi-basics"></a>Noções básicas sobre a GDI+  
 O <xref:System.Drawing.Graphics> classe fornece métodos para desenhar diversas formas, como círculos, triângulos, arcos e nas reticências, bem como métodos para exibir texto. O <xref:System.Drawing?displayProperty=nameWithType> namespace e seus subnamespaces contêm classes que encapsulam os elementos de gráficos como formas (círculos, retângulos, arcos e outros), cores, fontes, pincéis e assim por diante. Para obter mais informações sobre [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], consulte [Usando classes de elementos gráficos gerenciadas](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md). Os conceitos básicos de [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] também são descritos em [Como criar um controle do Windows Forms que mostre o progresso](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="geometry-of-the-drawing-region"></a>Geometria da região de desenho  
 O <xref:System.Windows.Forms.Control.ClientRectangle%2A> propriedade de um controle especifica a região retangular disponível para o controle na tela do usuário, enquanto o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriedade <xref:System.Windows.Forms.PaintEventArgs> Especifica a área que realmente é pintada. (Lembre-se de que a pintura é feita <xref:System.Windows.Forms.Control.Paint> método de evento que utiliza um <xref:System.Windows.Forms.PaintEventArgs> instância como seu argumento). Um controle pode precisar pintar apenas uma parte da sua área disponível, como é o caso quando uma pequena seção da exibição do controle é alterada. Nessas situações, um desenvolvedor do controle deve calcular o retângulo real para desenhar em e passá-lo para <xref:System.Windows.Forms.Control.Invalidate%2A>. As versões sobrecarregadas dos <xref:System.Windows.Forms.Control.Invalidate%2A> que levam um <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.Region> como um argumento, use esse argumento para gerar o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriedade <xref:System.Windows.Forms.PaintEventArgs>.  
  
 O fragmento de código a seguir mostra como o controle personalizado `FlashTrackBar` calcula a área retangular na qual desenhar. O `client` variável denota o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriedade. Para ver um exemplo completo, consulte [Como criar um controle do Windows Forms que mostre o progresso](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Liberando recursos gráficos  
 Objetos gráficos são caros porque usam recursos do sistema. Esses objetos incluem instâncias do <xref:System.Drawing.Graphics?displayProperty=nameWithType> classe, bem como instâncias de <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>e outras classes de elementos gráficos. É importante que você crie um recurso de gráfico somente quando precisar dele e o libere assim que terminar de usá-lo. Se você criar um tipo que implementa o <xref:System.IDisposable> interface, chame seu <xref:System.IDisposable.Dispose%2A> método quando tiver terminado com ela para liberar recursos.  
  
 Fragmento de código a seguir mostra como o `FlashTrackBar` controle personalizado cria e lança um <xref:System.Drawing.Brush> recursos. Para ver o código-fonte completo, consulte [Como criar um controle do Windows Forms que mostre o progresso](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Consulte também  
 [Como criar um controle do Windows Forms que mostre o progresso](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)
