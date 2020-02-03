---
title: Ponteiros do mouse
ms.date: 03/30/2017
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
ms.openlocfilehash: 4e8349effcd9b59045e39b763b4cb8b7d2fceb91
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740961"
---
# <a name="mouse-pointers-in-windows-forms"></a>Ponteiros do mouse no Windows Forms
O *ponteiro* do mouse, que às vezes é conhecido como o cursor, é um bitmap que especifica um ponto de foco na tela para entrada do usuário com o mouse. Este tópico fornece uma visão geral do ponteiro do mouse no Windows Forms e descreve algumas maneiras de modificar e controlar o ponteiro do mouse.  
  
## <a name="accessing-the-mouse-pointer"></a>Acessando o ponteiro do mouse  
 O ponteiro do mouse é representado pela classe <xref:System.Windows.Forms.Cursor>, e cada <xref:System.Windows.Forms.Control> tem uma propriedade <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> que especifica o ponteiro para esse controle. A classe <xref:System.Windows.Forms.Cursor> contém propriedades que descrevem o ponteiro, como as propriedades <xref:System.Windows.Forms.Cursor.Position%2A> e <xref:System.Windows.Forms.Cursor.HotSpot%2A>, e os métodos que podem modificar a aparência do ponteiro, como os métodos <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>e <xref:System.Windows.Forms.Cursor.DrawStretched%2A>.  
  
## <a name="controlling-the-mouse-pointer"></a>Controlando o ponteiro do mouse  
 Às vezes, pode ser recomendável limitar a área na qual o ponteiro do mouse pode ser usado ou alterar a posição do mouse. Você pode obter ou definir o local atual do mouse usando a propriedade <xref:System.Windows.Forms.Cursor.Position%2A> da <xref:System.Windows.Forms.Cursor>. Além disso, você pode limitar a área em que o ponteiro do mouse pode ser usado para definir a propriedade <xref:System.Windows.Forms.Cursor.Clip%2A>. A área de recorte, por padrão, é a tela inteira.  
  
## <a name="changing-the-mouse-pointer"></a>Alterando o ponteiro do mouse  
 Alterar o ponteiro do mouse é uma maneira importante de fornecer comentários para o usuário. Por exemplo, o ponteiro do mouse pode ser modificado nos manipuladores do <xref:System.Windows.Forms.Control.MouseEnter> e <xref:System.Windows.Forms.Control.MouseLeave> eventos para informar ao usuário que as computações estão ocorrendo e limitar a interação do usuário no controle. Às vezes, o ponteiro do mouse será alterado devido a eventos de sistema, como quando seu aplicativo está envolvido em uma operação do tipo "arrastar e soltar".  
  
 A principal maneira de alterar o ponteiro do mouse é definindo a propriedade <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.Control.DefaultCursor%2A> de um controle para uma nova <xref:System.Windows.Forms.Cursor>. Para obter exemplos de alteração do ponteiro do mouse, consulte o exemplo de código na classe <xref:System.Windows.Forms.Cursor>. Além disso, a classe <xref:System.Windows.Forms.Cursors> expõe um conjunto de objetos <xref:System.Windows.Forms.Cursor> para muitos tipos diferentes de ponteiros, como um ponteiro que se assemelha a uma mão. Para exibir o ponteiro de espera, que se assemelha a uma ampulheta, sempre que o ponteiro do mouse estiver no controle, use a propriedade <xref:System.Windows.Forms.Control.UseWaitCursor%2A> da classe <xref:System.Windows.Forms.Control>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Cursor>
- [Entrada do mouse em um Aplicativo do Windows Forms](mouse-input-in-a-windows-forms-application.md)
- [Funcionalidade do tipo "arrastar e soltar" no Windows Forms](drag-and-drop-functionality-in-windows-forms.md)
