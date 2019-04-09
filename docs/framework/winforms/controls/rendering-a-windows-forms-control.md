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
ms.openlocfilehash: 8de87e17d1baedccfe18bfded3ccab7ab59f0a09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125678"
---
# <a name="rendering-a-windows-forms-control"></a>Renderizando um controle dos Windows Forms
Renderização se refere ao processo de criar uma representação visual na tela do usuário. O Windows Forms usa [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] (a nova biblioteca de gráficos do Windows) para renderização. As classes gerenciadas que fornecem acesso aos [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] estão no <xref:System.Drawing?displayProperty=nameWithType> namespace e seus subnamespaces.  
  
 Os elementos a seguir estão envolvidos na renderização de controles:  
  
-   A funcionalidade de desenho fornecida pela classe base <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
-   Os elementos essenciais da biblioteca de gráficos [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
-   A geometria da região de desenho.  
  
-   O procedimento para liberar recursos gráficos.  
  
## <a name="drawing-functionality-provided-by-control"></a>Funcionalidade de desenho fornecida pelo controle  
 A classe base <xref:System.Windows.Forms.Control> fornece a funcionalidade de desenho por meio de seu <xref:System.Windows.Forms.Control.Paint> eventos. Um controle gera o <xref:System.Windows.Forms.Control.Paint> evento sempre que precisa atualizar sua exibição. Para obter mais informações sobre os eventos no .NET Framework, consulte [Tratando e gerando eventos](../../../standard/events/index.md).  
  
 Os dados do evento de classe para o <xref:System.Windows.Forms.Control.Paint> evento, <xref:System.Windows.Forms.PaintEventArgs>, contém os dados necessários para desenhar um controle — um identificador para um objeto gráfico e um objeto de retângulo que representa a região na qual desenhar. Esses objetos são mostrados em negrito no seguinte fragmento de código.  
  
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
  
 <xref:System.Drawing.Graphics> é uma classe gerenciada que encapsula a funcionalidade de desenho, conforme descrito na discussão sobre [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] mais adiante neste tópico. O <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> é uma instância do <xref:System.Drawing.Rectangle> estruturar e define a área disponível na qual um controle pode desenhar. Um desenvolvedor de controles pode calcular a <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> usando o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriedade de um controle, conforme descrito na discussão sobre geometria mais adiante neste tópico.  
  
 Um controle deve fornecer a lógica de renderização, substituindo o <xref:System.Windows.Forms.Control.OnPaint%2A> método que herda de <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.OnPaint%2A> obtém acesso a um objeto gráfico e um retângulo no qual desenhar por meio de <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> e o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriedades do <xref:System.Windows.Forms.PaintEventArgs> instância passada para ele.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 O <xref:System.Windows.Forms.Control.OnPaint%2A> método da base <xref:System.Windows.Forms.Control> classe não implementa nenhuma funcionalidade de desenho, mas simplesmente invoca representantes de eventos são registrados com o <xref:System.Windows.Forms.Control.Paint> eventos. Quando você substitui <xref:System.Windows.Forms.Control.OnPaint%2A>, você normalmente deve invocar o <xref:System.Windows.Forms.Control.OnPaint%2A> método da classe base, de modo que delegados registrados recebem o <xref:System.Windows.Forms.Control.Paint> eventos. No entanto, controles que pintam toda a sua superfície não devem chamar a classe base <xref:System.Windows.Forms.Control.OnPaint%2A>, pois isso causa cintilação. Para obter um exemplo de substituição de <xref:System.Windows.Forms.Control.OnPaint%2A> eventos, consulte o [como: Criar um controle de formulários do Windows que mostre o progresso](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
> [!NOTE]
>  Não invoque <xref:System.Windows.Forms.Control.OnPaint%2A> diretamente no seu controle; em vez disso, invoque o <xref:System.Windows.Forms.Control.Invalidate%2A> método (herdado de <xref:System.Windows.Forms.Control>) ou algum outro método que invoca <xref:System.Windows.Forms.Control.Invalidate%2A>. O <xref:System.Windows.Forms.Control.Invalidate%2A> por sua vez chama um método <xref:System.Windows.Forms.Control.OnPaint%2A>. O <xref:System.Windows.Forms.Control.Invalidate%2A> método está sobrecarregado e, dependendo dos argumentos fornecidos para <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, um controle redesenha parte ou toda a área de sua tela.  
  
 A base <xref:System.Windows.Forms.Control> classe define outro método que é útil para desenhar — o <xref:System.Windows.Forms.Control.OnPaintBackground%2A> método.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> Pinta a tela de fundo (e, portanto, a forma) da janela e é garantido que seja rápido, enquanto <xref:System.Windows.Forms.Control.OnPaint%2A> pinta os detalhes e pode ser mais lento porque as solicitações de pintura individuais são combinadas em um <xref:System.Windows.Forms.Control.Paint> evento que abrange todas as áreas que precisam ser redesenhado. Talvez você queira invocar o <xref:System.Windows.Forms.Control.OnPaintBackground%2A> se, por exemplo, você deseja desenhar um plano de fundo do gradiente de cores para o seu controle.  
  
 Embora <xref:System.Windows.Forms.Control.OnPaintBackground%2A> tem uma nomenclatura semelhante de eventos e usa o mesmo argumento que o `OnPaint` método, <xref:System.Windows.Forms.Control.OnPaintBackground%2A> não é um método de evento verdadeiro. Não há nenhuma `PaintBackground` evento e <xref:System.Windows.Forms.Control.OnPaintBackground%2A> não invoca representantes de eventos. Ao substituir a <xref:System.Windows.Forms.Control.OnPaintBackground%2A> método, uma classe derivada não é necessária para invocar o <xref:System.Windows.Forms.Control.OnPaintBackground%2A> método de sua classe base.  
  
## <a name="gdi-basics"></a>Noções básicas sobre a GDI+  
 O <xref:System.Drawing.Graphics> classe fornece métodos para desenhar várias formas, como círculos, triângulos, arcos e elipses, bem como métodos para exibir texto. O <xref:System.Drawing?displayProperty=nameWithType> namespace e seus namespaces secundários contêm classes que encapsulam elementos gráficos, como formas (círculos, retângulos, arcos e outros), cores, fontes, pincéis e assim por diante. Para obter mais informações sobre [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], consulte [Usando classes de elementos gráficos gerenciadas](../advanced/using-managed-graphics-classes.md). Os conceitos básicos de [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] também estão descritos no [como: Criar um controle de formulários do Windows que mostre o progresso](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="geometry-of-the-drawing-region"></a>Geometria da região de desenho  
 O <xref:System.Windows.Forms.Control.ClientRectangle%2A> propriedade de um controle especifica a região retangular disponível para o controle na tela do usuário, enquanto a <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriedade <xref:System.Windows.Forms.PaintEventArgs> Especifica a área que realmente é pintada. (Lembre-se de que a pintura é feita na <xref:System.Windows.Forms.Control.Paint> método de evento que usa um <xref:System.Windows.Forms.PaintEventArgs> instância como seu argumento). Um controle pode precisar pintar apenas uma parte da sua área disponível, como é o caso quando uma pequena seção da exibição do controle é alterada. Nessas situações, um desenvolvedor de controles deve calcular o retângulo real no qual desenhar e passá-lo para <xref:System.Windows.Forms.Control.Invalidate%2A>. As versões sobrecarregadas dos <xref:System.Windows.Forms.Control.Invalidate%2A> que aceitam uma <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.Region> como um argumento usam esse argumento para gerar o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriedade do <xref:System.Windows.Forms.PaintEventArgs>.  
  
 O fragmento de código a seguir mostra como o controle personalizado `FlashTrackBar` calcula a área retangular na qual desenhar. O `client` variável denota o <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriedade. Para obter um exemplo completo, consulte [como: Criar um controle de formulários do Windows que mostre o progresso](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Liberando recursos gráficos  
 Objetos gráficos são caros porque usam recursos do sistema. Esses objetos incluem instâncias do <xref:System.Drawing.Graphics?displayProperty=nameWithType> classe, bem como as instâncias do <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>e outras classes de elementos gráficos. É importante que você crie um recurso de gráfico somente quando precisar dele e o libere assim que terminar de usá-lo. Se você criar um tipo que implementa o <xref:System.IDisposable> interface, chame seu <xref:System.IDisposable.Dispose%2A> método quando tiver terminado com ela para liberar recursos.  
  
 Fragmento de código a seguir mostra como o `FlashTrackBar` controle personalizado cria e lança um <xref:System.Drawing.Brush> recursos. Para o código-fonte completo, consulte [como: Criar um controle de formulários do Windows que mostre o progresso](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Como: Criar um controle do Windows Forms que mostre o progresso](how-to-create-a-windows-forms-control-that-shows-progress.md)
