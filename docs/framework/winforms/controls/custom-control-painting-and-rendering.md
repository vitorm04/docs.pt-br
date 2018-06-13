---
title: Pintura e renderização de controle personalizada
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
ms.openlocfilehash: 18a05a739f42d41a650e66723f44aae69c1707c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526045"
---
# <a name="custom-control-painting-and-rendering"></a>Pintura e renderização de controle personalizada
A pintura personalizada de controles é uma das muitas tarefas complicadas que são facilitadas pelo .NET Framework. Ao criar um controle personalizado, você tem muitas opções em relação à aparência gráfica dele. Ao criar um controle que herda de `Control`, você deverá fornecer o código que permite ao controle renderizar sua representação gráfica. Ao criar um controle de usuário herdando de `UserControl` ou herdando de um dos controles dos Windows Forms, você pode substituir a representação gráfica padrão e fornecer seu próprio código de elementos gráficos. Se você deseja fornecer renderização personalizada para os controles membros de um `UserControl` que você está criando, suas opções tornam-se mais limitadas, mas ainda proporcionam uma ampla gama de possibilidades gráficas para seus aplicativos e controles.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Renderizando um controle dos Windows Forms](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 Mostra como programar a lógica que exibe um controle.  
  
 [Controles desenhados pelo usuário](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 Fornece uma visão geral das etapas necessárias para escrever e substituir um código de renderização para o seu controle.  
  
 [Controles constituintes](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 Descreve como implementar o código de renderização personalizada para controles membros em seus formulários e controles de usuário.  
  
 [Como deixar o controle invisível no tempo de execução](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 Mostra como usar o <xref:System.Windows.Forms.Control.Visible%2A> propriedade para ocultar e mostrar um controle.  
  
 [Como dar ao controle uma tela de fundo transparente](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 Mostra como usar o <xref:System.Windows.Forms.Control.SetStyle%2A> método para criar uma cor de plano de fundo transparente, parcialmente transparente ou opaco.  
  
 [Renderizando controles com estilos visuais](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 Mostra como renderizar controles com estilos visuais em sistemas operacionais que dão suporte a eles.  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.Control>  
 Descreve essa classe e tem links para todos os seus membros.  
  
 <xref:System.Windows.Forms.UserControl>  
 Descreve essa classe e tem links para todos os seus membros.  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 Descreve esse método.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Como Criar Objetos Gráficos para Desenho](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 Apresenta a funcionalidade de elementos gráficos [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] de uma perspectiva do Visual Studio e fornece links para obter mais informações.  
  
 [Variedades de controles personalizados](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 Descreve os tipos de controles personalizados que você pode criar.
