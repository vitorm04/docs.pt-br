---
title: Renderizar um controle
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
ms.openlocfilehash: 0e1a7ca5dc0414d518c081b1db2dca5477d4f743
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742389"
---
# <a name="rendering-a-windows-forms-control"></a>Renderizando um controle dos Windows Forms
Renderização se refere ao processo de criar uma representação visual na tela do usuário. Windows Forms usa GDI (a nova biblioteca de gráficos do Windows) para renderização. As classes gerenciadas que fornecem acesso ao GDI estão no namespace <xref:System.Drawing?displayProperty=nameWithType> e em seus subnamespaces.  
  
 Os elementos a seguir estão envolvidos na renderização de controles:  
  
- A funcionalidade de desenho fornecida pela classe base <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
- Os elementos essenciais da biblioteca gráfica GDI.  
  
- A geometria da região de desenho.  
  
- O procedimento para liberar recursos gráficos.  
  
## <a name="drawing-functionality-provided-by-control"></a>Funcionalidade de desenho fornecida pelo controle  
 A classe base <xref:System.Windows.Forms.Control> fornece a funcionalidade de desenho por meio de seu evento <xref:System.Windows.Forms.Control.Paint>. Um controle gera o evento <xref:System.Windows.Forms.Control.Paint> sempre que ele precisa atualizar sua exibição. Para obter mais informações sobre os eventos no .NET Framework, consulte [Tratando e gerando eventos](../../../standard/events/index.md).  
  
 A classe de dados de evento para o evento <xref:System.Windows.Forms.Control.Paint>, <xref:System.Windows.Forms.PaintEventArgs>, contém os dados necessários para desenhar um controle — um identificador para um objeto de gráfico e um objeto de retângulo que representa a região na qual desenhar. Esses objetos são mostrados em negrito no seguinte fragmento de código.  
  
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
  
 <xref:System.Drawing.Graphics> é uma classe gerenciada que encapsula a funcionalidade de desenho, conforme descrito na discussão do GDI mais adiante neste tópico. O <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> é uma instância da estrutura de <xref:System.Drawing.Rectangle> e define a área disponível na qual um controle pode desenhar. Um desenvolvedor de controle pode calcular o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> usando a propriedade <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> de um controle, conforme descrito na discussão de geometry mais adiante neste tópico.  
  
 Um controle deve fornecer a lógica de renderização substituindo o método <xref:System.Windows.Forms.Control.OnPaint%2A> que ele herda de <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.OnPaint%2A> obtém acesso a um objeto de gráfico e um retângulo para desenhar por meio da <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> e as propriedades de <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> da instância de <xref:System.Windows.Forms.PaintEventArgs> passada para ele.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 O método <xref:System.Windows.Forms.Control.OnPaint%2A> da classe base <xref:System.Windows.Forms.Control> não implementa nenhuma funcionalidade de desenho, mas meramente invoca os delegados de evento que são registrados com o evento <xref:System.Windows.Forms.Control.Paint>. Quando você substitui <xref:System.Windows.Forms.Control.OnPaint%2A>, normalmente você deve invocar o método <xref:System.Windows.Forms.Control.OnPaint%2A> da classe base para que os delegados registrados recebam o evento <xref:System.Windows.Forms.Control.Paint>. No entanto, os controles que pintam toda a superfície não devem invocar a <xref:System.Windows.Forms.Control.OnPaint%2A>da classe base, pois isso apresenta cintilação. Para obter um exemplo de substituição do evento <xref:System.Windows.Forms.Control.OnPaint%2A>, consulte o [como criar um controle de Windows Forms que mostra o progresso](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
> [!NOTE]
> Não invocar <xref:System.Windows.Forms.Control.OnPaint%2A> diretamente do seu controle; em vez disso, invoque o método <xref:System.Windows.Forms.Control.Invalidate%2A> (Herdado de <xref:System.Windows.Forms.Control>) ou algum outro método que invoque <xref:System.Windows.Forms.Control.Invalidate%2A>. O método <xref:System.Windows.Forms.Control.Invalidate%2A>, por sua vez, invoca <xref:System.Windows.Forms.Control.OnPaint%2A>. O método <xref:System.Windows.Forms.Control.Invalidate%2A> está sobrecarregado e, dependendo dos argumentos fornecidos para <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, um controle redesenha qualquer parte ou toda a sua área da tela.  
  
 A classe base <xref:System.Windows.Forms.Control> define outro método que é útil para o desenho — o método <xref:System.Windows.Forms.Control.OnPaintBackground%2A>.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> pinta o plano de fundo (e, portanto, a forma) da janela e tem a garantia de ser rápida, enquanto <xref:System.Windows.Forms.Control.OnPaint%2A> pinta os detalhes e pode ser mais lento porque as solicitações de pintura individuais são combinadas em um evento <xref:System.Windows.Forms.Control.Paint> que abrange todas as áreas que precisam ser redesenhadas. Talvez você queira invocar a <xref:System.Windows.Forms.Control.OnPaintBackground%2A> se, por exemplo, desejar desenhar um plano de fundo colorido por gradiente para seu controle.  
  
 Embora <xref:System.Windows.Forms.Control.OnPaintBackground%2A> tenha um evento como nomenclatura e usa o mesmo argumento que o método `OnPaint`, <xref:System.Windows.Forms.Control.OnPaintBackground%2A> não é um método de evento verdadeiro. Não há evento `PaintBackground` e <xref:System.Windows.Forms.Control.OnPaintBackground%2A> não invoca delegados de eventos. Ao substituir o método <xref:System.Windows.Forms.Control.OnPaintBackground%2A>, uma classe derivada não é necessária para invocar o método <xref:System.Windows.Forms.Control.OnPaintBackground%2A> de sua classe base.  
  
## <a name="gdi-basics"></a>Noções básicas sobre a GDI+  
 A classe <xref:System.Drawing.Graphics> fornece métodos para desenhar várias formas, como círculos, triângulos, arcos e elipses, bem como métodos para exibir texto. O namespace <xref:System.Drawing?displayProperty=nameWithType> e seus subnamespaces contêm classes que encapsulam elementos gráficos, como formas (círculos, retângulos, arcos e outros), cores, fontes, pincéis e assim por diante. Para obter mais informações sobre o GDI, consulte [usando classes de gráficos gerenciados](../advanced/using-managed-graphics-classes.md). Os conceitos básicos do GDI também são descritos no [como criar um Windows Forms controle que mostra o progresso](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="geometry-of-the-drawing-region"></a>Geometria da região de desenho  
 A propriedade <xref:System.Windows.Forms.Control.ClientRectangle%2A> de um controle Especifica a região retangular disponível para o controle na tela do usuário, enquanto a propriedade <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> de <xref:System.Windows.Forms.PaintEventArgs> especifica a área que é realmente pintada. (Lembre-se de que a pintura é feita no método de evento <xref:System.Windows.Forms.Control.Paint> que usa uma instância <xref:System.Windows.Forms.PaintEventArgs> como seu argumento). Um controle pode precisar pintar apenas uma parte da sua área disponível, como é o caso quando uma pequena seção da exibição do controle é alterada. Nessas situações, um desenvolvedor de controle deve calcular o retângulo real para desenhar e passá-lo para <xref:System.Windows.Forms.Control.Invalidate%2A>. As versões sobrecarregadas do <xref:System.Windows.Forms.Control.Invalidate%2A> que usam um <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.Region> como um argumento usam esse argumento para gerar a propriedade <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> de <xref:System.Windows.Forms.PaintEventArgs>.  
  
 O fragmento de código a seguir mostra como o controle personalizado `FlashTrackBar` calcula a área retangular na qual desenhar. A variável `client` denota a propriedade <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>. Para ver um exemplo completo, consulte [Como criar um controle do Windows Forms que mostre o progresso](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Liberando recursos gráficos  
 Objetos gráficos são caros porque usam recursos do sistema. Esses objetos incluem instâncias da classe <xref:System.Drawing.Graphics?displayProperty=nameWithType>, bem como instâncias de <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>e outras classes gráficas. É importante que você crie um recurso de gráfico somente quando precisar dele e o libere assim que terminar de usá-lo. Se você criar um tipo que implemente a interface <xref:System.IDisposable>, chame seu método <xref:System.IDisposable.Dispose%2A> quando terminar com ele para liberar recursos.  
  
 O fragmento de código a seguir mostra como o controle personalizado `FlashTrackBar` cria e libera um recurso de <xref:System.Drawing.Brush>. Para ver o código-fonte completo, consulte [Como criar um controle do Windows Forms que mostre o progresso](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Como criar um controle do Windows Forms que mostre o progresso](how-to-create-a-windows-forms-control-that-shows-progress.md)
