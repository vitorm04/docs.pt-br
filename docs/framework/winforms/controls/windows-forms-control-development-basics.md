---
title: Noções básicas para o desenvolvimento de controles
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
ms.openlocfilehash: fab0a76e2f9fdb7e2f89e9d6a10dd9c522a6d8e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739920"
---
# <a name="windows-forms-control-development-basics"></a>Noções básicas sobre o desenvolvimento de controle dos Windows Forms
Um controle de Windows Forms é uma classe que deriva direta ou indiretamente de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. A lista a seguir descreve os cenários comuns para o desenvolvimento de controles do Windows Forms:  
  
- Combinando controles existentes para criar um controle composto.  
  
     Controles compostos encapsulam uma interface do usuário que pode ser reutilizada como um controle. Um exemplo de um controle composto é um controle que consiste em uma caixa de texto e um botão de redefinição. Designers visuais dão suporte avançado para a criação de controles compostos. Para criar um controle composto, derive de <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>. A classe base <xref:System.Windows.Forms.UserControl> fornece roteamento de teclado para controles filho e permite que controles filho funcionem como um grupo. Para obter mais informações, consulte [Desenvolvendo um controle dos Windows Forms de composição](developing-a-composite-windows-forms-control.md).  
  
- Estendendo um controle existente para personalizá-la ou aumentar sua funcionalidade.  
  
     Um botão cuja cor não pode ser alterado e um botão que tem uma propriedade adicional que controla quantas vezes ele foi clicado são exemplos de controles estendidos. Você pode personalizar qualquer controle do Windows Forms derivado dele e substituir ou adicionar propriedades, métodos e eventos.  
  
- Criando um controle que não combina ou estende os controles existentes.  
  
     Nesse cenário, derive seu controle da classe base <xref:System.Windows.Forms.Control>. Você pode adicionar e substituir propriedades, métodos e eventos da classe base. Para começar, consulte [Como desenvolver um controle simples do Windows Forms](how-to-develop-a-simple-windows-forms-control.md).  
  
 A classe base para controles de Windows Forms, <xref:System.Windows.Forms.Control>, fornece o direcionamento necessário para a exibição Visual em aplicativos baseados no Windows no lado do cliente. o <xref:System.Windows.Forms.Control> fornece um identificador de janela, manipula o roteamento de mensagens e fornece eventos de mouse e teclado, bem como muitos outros eventos de interface do usuário. Ele fornece layout avançado e tem propriedades específicas para a exibição Visual, como <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>e muitos outros. Além disso, ele fornece segurança, suporte a threading e interoperabilidade com controles ActiveX. Como grande parte da infraestrutura é fornecida pela classe base, é relativamente fácil desenvolver seus próprios controles dos Windows Forms.  
  
## <a name="see-also"></a>Veja também

- [Como desenvolver um controle simples dos Windows Forms](how-to-develop-a-simple-windows-forms-control.md)
- [Desenvolvendo um controle de composição dos Windows Forms](developing-a-composite-windows-forms-control.md)
- [Como criar um controle dos Windows Forms que mostre o progresso](how-to-create-a-windows-forms-control-that-shows-progress.md)
- [Variedades de Controles Personalizados](varieties-of-custom-controls.md)
