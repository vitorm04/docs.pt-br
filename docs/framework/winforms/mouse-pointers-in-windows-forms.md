---
title: Ponteiros do mouse no Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aaca18bff265fafbb5bad26adfe2a8c490d85132
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="mouse-pointers-in-windows-forms"></a>Ponteiros do mouse no Windows Forms
O *ponteiro* do mouse, que às vezes é conhecido como o cursor, é um bitmap que especifica um ponto de foco na tela para entrada do usuário com o mouse. Este tópico fornece uma visão geral do ponteiro do mouse no Windows Forms e descreve algumas maneiras de modificar e controlar o ponteiro do mouse.  
  
## <a name="accessing-the-mouse-pointer"></a>Acessando o ponteiro do mouse  
 O ponteiro do mouse é representado pelo <xref:System.Windows.Forms.Cursor> classe e cada <xref:System.Windows.Forms.Control> tem um <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> propriedade que especifica o ponteiro para o controle. O <xref:System.Windows.Forms.Cursor> classe contém propriedades que descrevem o ponteiro, como o <xref:System.Windows.Forms.Cursor.Position%2A> e <xref:System.Windows.Forms.Cursor.HotSpot%2A> propriedades e métodos que podem modificar a aparência do ponteiro, como o <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>, e <xref:System.Windows.Forms.Cursor.DrawStretched%2A> métodos.  
  
## <a name="controlling-the-mouse-pointer"></a>Controlando o ponteiro do mouse  
 Às vezes, pode ser recomendável limitar a área na qual o ponteiro do mouse pode ser usado ou alterar a posição do mouse. Você pode obter ou definir o local atual do mouse usando o <xref:System.Windows.Forms.Cursor.Position%2A> propriedade o <xref:System.Windows.Forms.Cursor>. Além disso, você pode limitar a área em que o ponteiro do mouse pode ser usado ser configuração o <xref:System.Windows.Forms.Cursor.Clip%2A> propriedade. A área de recorte, por padrão, é a tela inteira.  
  
## <a name="changing-the-mouse-pointer"></a>Alterando o ponteiro do mouse  
 Alterar o ponteiro do mouse é uma maneira importante de fornecer comentários para o usuário. Por exemplo, o ponteiro do mouse pode ser modificado nos manipuladores do <xref:System.Windows.Forms.Control.MouseEnter> e <xref:System.Windows.Forms.Control.MouseLeave> eventos para informar ao usuário que computações estão ocorrendo e para limitar a interação do usuário no controle. Às vezes, o ponteiro do mouse será alterado devido a eventos de sistema, como quando seu aplicativo está envolvido em uma operação do tipo "arrastar e soltar".  
  
 A principal maneira de alterar o ponteiro do mouse está definindo o <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.Control.DefaultCursor%2A> propriedade de um controle para um novo <xref:System.Windows.Forms.Cursor>. Para obter exemplos de alteração do ponteiro do mouse, consulte o exemplo de código no <xref:System.Windows.Forms.Cursor> classe. Além disso, o <xref:System.Windows.Forms.Cursors> classe expõe um conjunto de <xref:System.Windows.Forms.Cursor> objetos para muitos tipos diferentes de ponteiros, como um ponteiro que se parece com um símbolo de mão. Para exibir o ponteiro de espera, que se parece com uma ampulheta, sempre que o ponteiro do mouse está sobre o controle, use o <xref:System.Windows.Forms.Control.UseWaitCursor%2A> propriedade o <xref:System.Windows.Forms.Control> classe.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Cursor>  
 [Entrada do mouse em um Aplicativo do Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 [Funcionalidade do tipo "arrastar e soltar" no Windows Forms](../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)
