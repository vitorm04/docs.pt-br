---
title: Noções básicas sobre o desenvolvimento de controle dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
ms.openlocfilehash: b455912468376d2f5de0ac1f30b4fcab5bb93309
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541135"
---
# <a name="windows-forms-control-development-basics"></a>Noções básicas sobre o desenvolvimento de controle dos Windows Forms
Um controle de formulários do Windows é uma classe que deriva diretamente ou indiretamente de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. A lista a seguir descreve os cenários comuns para o desenvolvimento de controles do Windows Forms:  
  
-   Combinando controles existentes para criar um controle composto.  
  
     Controles compostos encapsulam uma interface do usuário que pode ser reutilizada como um controle. Um exemplo de um controle composto é um controle que consiste em uma caixa de texto e um botão de redefinição. Designers visuais dão suporte avançado para a criação de controles compostos. Para criar um controle composto, derivam <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>. A classe base <xref:System.Windows.Forms.UserControl> fornece o roteamento de teclado para controles e permite que os controles filho funcionar como um grupo filho. Para obter mais informações, consulte [Desenvolvendo um controle composto do Windows Forms](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).  
  
-   Estendendo um controle existente para personalizá-la ou aumentar sua funcionalidade.  
  
     Um botão cuja cor não pode ser alterado e um botão que tem uma propriedade adicional que controla quantas vezes ele foi clicado são exemplos de controles estendidos. Você pode personalizar qualquer controle do Windows Forms derivado dele e substituir ou adicionar propriedades, métodos e eventos.  
  
-   Criando um controle que não combina ou estende os controles existentes.  
  
     Nesse cenário, o controle é derivado da classe base <xref:System.Windows.Forms.Control>. Você pode adicionar e substituir propriedades, métodos e eventos da classe base. Para começar, consulte [Como desenvolver um controle simples do Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).  
  
 A classe base para controles de formulários do Windows, <xref:System.Windows.Forms.Control>, fornece os detalhes necessários para a exibição visual em aplicativos do lado do cliente Windows. <xref:System.Windows.Forms.Control> Fornece um identificador de janela, manipula o roteamento de mensagens e fornece eventos de mouse e teclado, assim como muitos outros usuário eventos de interface. Ele fornece o layout avançado e tem propriedades específicas para a exibição visual, como <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>e muitos outros. Além disso, ele fornece segurança, suporte a threading e interoperabilidade com controles ActiveX. Como grande parte da infraestrutura é fornecida pela classe base, é relativamente fácil desenvolver seus próprios controles do Windows Forms.  
  
## <a name="see-also"></a>Consulte também  
 [Como desenvolver um controle simples dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [Desenvolvendo um controle de composição dos Windows Forms](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)  
 [Como criar um controle dos Windows Forms que mostre o progresso](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)  
 [Variedades de controles personalizados](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
