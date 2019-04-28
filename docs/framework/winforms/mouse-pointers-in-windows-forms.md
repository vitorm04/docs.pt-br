---
title: Ponteiros do mouse no Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
ms.openlocfilehash: e9b572ba40618a72b8db58917008ebd61a23de79
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800760"
---
# <a name="mouse-pointers-in-windows-forms"></a>Ponteiros do mouse no Windows Forms
O *ponteiro* do mouse, que às vezes é conhecido como o cursor, é um bitmap que especifica um ponto de foco na tela para entrada do usuário com o mouse. Este tópico fornece uma visão geral do ponteiro do mouse no Windows Forms e descreve algumas maneiras de modificar e controlar o ponteiro do mouse.  
  
## <a name="accessing-the-mouse-pointer"></a>Acessando o ponteiro do mouse  
 O ponteiro do mouse é representado pela <xref:System.Windows.Forms.Cursor> classe e cada <xref:System.Windows.Forms.Control> tem um <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> propriedade que especifica o ponteiro para o controle. O <xref:System.Windows.Forms.Cursor> classe contém propriedades que descrevem o ponteiro, como o <xref:System.Windows.Forms.Cursor.Position%2A> e <xref:System.Windows.Forms.Cursor.HotSpot%2A> propriedades e métodos que podem modificar a aparência do ponteiro, como o <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>, e <xref:System.Windows.Forms.Cursor.DrawStretched%2A> métodos.  
  
## <a name="controlling-the-mouse-pointer"></a>Controlando o ponteiro do mouse  
 Às vezes, pode ser recomendável limitar a área na qual o ponteiro do mouse pode ser usado ou alterar a posição do mouse. Você pode obter ou definir o local atual do mouse usando o <xref:System.Windows.Forms.Cursor.Position%2A> propriedade do <xref:System.Windows.Forms.Cursor>. Além disso, você pode limitar a área em que o ponteiro do mouse pode ser usado ser configuração o <xref:System.Windows.Forms.Cursor.Clip%2A> propriedade. A área de recorte, por padrão, é a tela inteira.  
  
## <a name="changing-the-mouse-pointer"></a>Alterando o ponteiro do mouse  
 Alterar o ponteiro do mouse é uma maneira importante de fornecer comentários para o usuário. Por exemplo, o ponteiro do mouse pode ser modificado nos manipuladores dos <xref:System.Windows.Forms.Control.MouseEnter> e <xref:System.Windows.Forms.Control.MouseLeave> eventos para informar ao usuário que computações estão ocorrendo e para limitar a interação do usuário no controle. Às vezes, o ponteiro do mouse será alterado devido a eventos de sistema, como quando seu aplicativo está envolvido em uma operação do tipo "arrastar e soltar".  
  
 A principal maneira de alterar o ponteiro do mouse está definindo o <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.Control.DefaultCursor%2A> propriedade de um controle para um novo <xref:System.Windows.Forms.Cursor>. Para obter exemplos de alterar o ponteiro do mouse, consulte o exemplo de código a <xref:System.Windows.Forms.Cursor> classe. Além disso, o <xref:System.Windows.Forms.Cursors> classe expõe um conjunto de <xref:System.Windows.Forms.Cursor> objetos para muitos tipos diferentes de ponteiros, como um ponteiro que lembra uma mão. Para exibir o ponteiro de espera, que lembra uma ampulheta, sempre que o ponteiro do mouse está sobre o controle, use o <xref:System.Windows.Forms.Control.UseWaitCursor%2A> propriedade do <xref:System.Windows.Forms.Control> classe.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Cursor>
- [Entrada do mouse em um Aplicativo do Windows Forms](mouse-input-in-a-windows-forms-application.md)
- [Funcionalidade do tipo "arrastar e soltar" no Windows Forms](drag-and-drop-functionality-in-windows-forms.md)
