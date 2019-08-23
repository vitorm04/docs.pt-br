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
ms.openlocfilehash: b24fbefac0dcfb666e25ad1d1726ef2cf8a5d84e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968270"
---
# <a name="rendering-a-windows-forms-control"></a>Renderizando um controle dos Windows Forms
Renderização se refere ao processo de criar uma representação visual na tela do usuário. Windows Forms usa GDI (a nova biblioteca de gráficos do Windows) para renderização. As classes gerenciadas que fornecem acesso ao GDI estão no <xref:System.Drawing?displayProperty=nameWithType> namespace e em seus subnamespaces.  
  
 Os elementos a seguir estão envolvidos na renderização de controles:  
  
- A funcionalidade de desenho fornecida pela classe <xref:System.Windows.Forms.Control?displayProperty=nameWithType>base.  
  
- Os elementos essenciais da biblioteca gráfica GDI.  
  
- A geometria da região de desenho.  
  
- O procedimento para liberar recursos gráficos.  
  
## <a name="drawing-functionality-provided-by-control"></a>Funcionalidade de desenho fornecida pelo controle  
 A classe <xref:System.Windows.Forms.Control> base fornece a funcionalidade de desenho <xref:System.Windows.Forms.Control.Paint> por meio de seu evento. Um controle gera o <xref:System.Windows.Forms.Control.Paint> evento sempre que precisa atualizar sua exibição. Para obter mais informações sobre os eventos no .NET Framework, consulte [Tratando e gerando eventos](../../../standard/events/index.md).  
  
 A classe de dados de evento <xref:System.Windows.Forms.Control.Paint> para o <xref:System.Windows.Forms.PaintEventArgs>evento,, mantém os dados necessários para desenhar um controle — um identificador para um objeto de gráfico e um objeto de retângulo que representa a região na qual desenhar. Esses objetos são mostrados em negrito no seguinte fragmento de código.  
  
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
  
 <xref:System.Drawing.Graphics>é uma classe gerenciada que encapsula a funcionalidade de desenho, conforme descrito na discussão do GDI mais adiante neste tópico. O <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> é uma instância <xref:System.Drawing.Rectangle> da estrutura e define a área disponível na qual um controle pode desenhar. Um desenvolvedor de controle pode calcular <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> o usando <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> a propriedade de um controle, conforme descrito na discussão sobre Geometry mais adiante neste tópico.  
  
 Um controle deve fornecer lógica de renderização substituindo <xref:System.Windows.Forms.Control.OnPaint%2A> o método do <xref:System.Windows.Forms.Control>qual ele herda. <xref:System.Windows.Forms.Control.OnPaint%2A>Obtém acesso a um objeto de gráfico e um retângulo para desenhar por meio <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> de e <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> as propriedades da <xref:System.Windows.Forms.PaintEventArgs> instância passada a ele.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 O <xref:System.Windows.Forms.Control.OnPaint%2A> método da classe base <xref:System.Windows.Forms.Control> não implementa nenhuma funcionalidade de desenho, mas meramente invoca os delegados de evento que são registrados com o <xref:System.Windows.Forms.Control.Paint> evento. Ao substituir <xref:System.Windows.Forms.Control.OnPaint%2A>, você normalmente deve invocar o <xref:System.Windows.Forms.Control.OnPaint%2A> método da classe base para que os delegados registrados recebam <xref:System.Windows.Forms.Control.Paint> o evento. No entanto, os controles que pintam toda a superfície não devem invocar a classe <xref:System.Windows.Forms.Control.OnPaint%2A>base, pois isso apresenta cintilação. Para obter um exemplo de substituição <xref:System.Windows.Forms.Control.OnPaint%2A> do evento, [consulte: Crie um controle de Windows Forms que mostre](how-to-create-a-windows-forms-control-that-shows-progress.md)o progresso.  
  
> [!NOTE]
> Não invoque <xref:System.Windows.Forms.Control.OnPaint%2A> diretamente do seu controle; em vez disso, invoque <xref:System.Windows.Forms.Control.Invalidate%2A> o método (Herdado de <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms.Control.Invalidate%2A>) ou algum outro método que invoca. O <xref:System.Windows.Forms.Control.Invalidate%2A> método, por sua vez <xref:System.Windows.Forms.Control.OnPaint%2A>, invoca. O <xref:System.Windows.Forms.Control.Invalidate%2A> método está sobrecarregado e, dependendo dos argumentos fornecidos para <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, um controle redesenha qualquer parte ou toda a sua área de tela.  
  
 A classe <xref:System.Windows.Forms.Control> base define outro método que é útil para desenhar — o <xref:System.Windows.Forms.Control.OnPaintBackground%2A> método.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A>pinta o plano de fundo (e, portanto, a forma) da janela e é garantido que seja <xref:System.Windows.Forms.Control.OnPaint%2A> rápido, enquanto pinta os detalhes e pode ser mais lento porque as solicitações de pintura <xref:System.Windows.Forms.Control.Paint> individuais são combinadas em um evento que abrange todas as áreas que precisam ser redesenhado. Talvez você queira invocar o <xref:System.Windows.Forms.Control.OnPaintBackground%2A> If, por exemplo, que deseja desenhar um plano de fundo colorido em gradiente para seu controle.  
  
 Embora <xref:System.Windows.Forms.Control.OnPaintBackground%2A> tenha um evento como nomenclatura e assuma o mesmo argumento que o `OnPaint` método, <xref:System.Windows.Forms.Control.OnPaintBackground%2A> não é um método de evento verdadeiro. Não há <xref:System.Windows.Forms.Control.OnPaintBackground%2A> evento e não invoca os delegados de evento. `PaintBackground` Ao substituir o <xref:System.Windows.Forms.Control.OnPaintBackground%2A> método, uma classe derivada não é necessária para invocar <xref:System.Windows.Forms.Control.OnPaintBackground%2A> o método de sua classe base.  
  
## <a name="gdi-basics"></a>Noções básicas sobre a GDI+  
 A <xref:System.Drawing.Graphics> classe fornece métodos para desenhar várias formas, como círculos, triângulos, arcos e elipses, bem como métodos para exibir texto. O <xref:System.Drawing?displayProperty=nameWithType> namespace e seus subnamespaces contêm classes que encapsulam elementos gráficos, como formas (círculos, retângulos, arcos e outros), cores, fontes, pincéis e assim por diante. Para obter mais informações sobre o GDI, consulte [usando classes de gráficos gerenciados](../advanced/using-managed-graphics-classes.md). Os conceitos básicos do GDI também são descritos no [How to: Crie um controle de Windows Forms que mostre](how-to-create-a-windows-forms-control-that-shows-progress.md)o progresso.  
  
## <a name="geometry-of-the-drawing-region"></a>Geometria da região de desenho  
 A <xref:System.Windows.Forms.Control.ClientRectangle%2A> propriedade de um controle Especifica a região retangular disponível para o controle na tela do usuário, enquanto a <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriedade de <xref:System.Windows.Forms.PaintEventArgs> especifica a área que é realmente pintada. (Lembre-se de que a pintura <xref:System.Windows.Forms.Control.Paint> é feita no método de <xref:System.Windows.Forms.PaintEventArgs> evento que usa uma instância como seu argumento). Um controle pode precisar pintar apenas uma parte da sua área disponível, como é o caso quando uma pequena seção da exibição do controle é alterada. Nessas situações, um desenvolvedor de controle deve calcular o retângulo real para desenhar e passá-lo <xref:System.Windows.Forms.Control.Invalidate%2A>para. As versões sobrecarregadas do <xref:System.Windows.Forms.Control.Invalidate%2A> que usam um <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.Region> como um argumento usam esse argumento para gerar a <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriedade de <xref:System.Windows.Forms.PaintEventArgs>.  
  
 O fragmento de código a seguir mostra como o controle personalizado `FlashTrackBar` calcula a área retangular na qual desenhar. A `client` variável denota a <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriedade. Para obter um exemplo completo, [consulte Como: Crie um controle de Windows Forms que mostre](how-to-create-a-windows-forms-control-that-shows-progress.md)o progresso.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Liberando recursos gráficos  
 Objetos gráficos são caros porque usam recursos do sistema. Esses objetos incluem instâncias da <xref:System.Drawing.Graphics?displayProperty=nameWithType> classe, bem como instâncias de <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>e outras classes gráficas. É importante que você crie um recurso de gráfico somente quando precisar dele e o libere assim que terminar de usá-lo. Se você criar um tipo que implementa a <xref:System.IDisposable> interface, chame seu <xref:System.IDisposable.Dispose%2A> método quando terminar de fazê-lo para liberar recursos.  
  
 O fragmento de código a seguir mostra `FlashTrackBar` como o controle personalizado cria e <xref:System.Drawing.Brush> libera um recurso. Para obter o código-fonte completo [, consulte Como: Crie um controle de Windows Forms que mostre](how-to-create-a-windows-forms-control-that-shows-progress.md)o progresso.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Como: Criar um controle de Windows Forms que mostra o progresso](how-to-create-a-windows-forms-control-that-shows-progress.md)
