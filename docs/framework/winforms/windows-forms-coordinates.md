---
title: Coordenadas do Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
ms.openlocfilehash: ba6bf8c1a8ae5ab14a9b33ae431e34310046b2a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537870"
---
# <a name="windows-forms-coordinates"></a>Coordenadas do Windows Forms
O sistema de coordenadas para um Windows Form é baseado nas coordenadas de dispositivo e a unidade básica de medida de desenho no Windows Forms é a unidade do dispositivo (normalmente, o pixel). Pontos na tela são descritos por pares de coordenadas x e y, com as coordenadas x aumentando para a direita e coordenadas y aumentando de cima para baixo. O local de origem, em relação à tela, variará dependendo se você está especificando as coordenadas de tela ou de cliente.  
  
## <a name="screen-coordinates"></a>Coordenadas de tela  
 Um Aplicativo do Windows Forms especifica a posição de uma janela na tela em coordenadas de tela. Para coordenadas de tela, a origem é o canto superior esquerdo da tela. A posição completa de uma janela é geralmente descrita por um <xref:System.Drawing.Rectangle> estrutura que contém as coordenadas de tela de dois pontos que definem os cantos superior esquerdo e direito inferior da janela.  
  
## <a name="client-coordinates"></a>Coordenadas de cliente  
 Um Aplicativo do Windows Forms especifica a posição dos pontos em um formulário ou controle usando coordenadas de cliente. A origem das coordenadas de cliente é o canto superior esquerdo da área de cliente do controle ou formulário. Coordenadas de cliente garantem que um aplicativo pode usar valores de coordenadas consistentes ao desenhar em um formulário ou controle, independentemente da posição do formulário ou controle na tela.  
  
 As dimensões da área cliente também são descritas por um <xref:System.Drawing.Rectangle> estrutura que contém as coordenadas do cliente para a área. Em todos os casos, a coordenada superior esquerda do retângulo está incluída na área de cliente, enquanto a coordenada inferior direita é excluída. Operações de elementos gráficos não incluem bordas direita e inferiores de uma área de cliente. Por exemplo o <xref:System.Drawing.Graphics.FillRectangle%2A> método preencherá até a borda direita e inferior do retângulo especificado, mas não incluirá essas bordas.  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>Mapeamento de um tipo de coordenada para outro  
 Ocasionalmente, pode ser recomendável mapear das coordenadas de tela para as coordenadas de cliente. Você pode fazer isso facilmente usando o <xref:System.Windows.Forms.Control.PointToClient%2A> e <xref:System.Windows.Forms.Control.PointToScreen%2A> métodos disponíveis a <xref:System.Windows.Forms.Control> classe. Por exemplo, o <xref:System.Windows.Forms.Control.MousePosition%2A> propriedade <xref:System.Windows.Forms.Control> é relatada em coordenadas da tela, mas você pode convertê-los para coordenadas do cliente.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Control.PointToClient%2A>  
 <xref:System.Windows.Forms.Control.PointToScreen%2A>
