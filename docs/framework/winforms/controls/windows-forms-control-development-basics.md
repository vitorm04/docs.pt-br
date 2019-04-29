---
title: Noções básicas sobre o desenvolvimento de controle dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
ms.openlocfilehash: 21b8b08e56e8b4d48fb738b86247d3f04dc4150b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759863"
---
# <a name="windows-forms-control-development-basics"></a>Noções básicas sobre o desenvolvimento de controle dos Windows Forms
Um controle dos Windows Forms é uma classe que deriva direta ou indiretamente <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. A lista a seguir descreve os cenários comuns para o desenvolvimento de controles do Windows Forms:  
  
- Combinando controles existentes para criar um controle composto.  
  
     Controles compostos encapsulam uma interface do usuário que pode ser reutilizada como um controle. Um exemplo de um controle composto é um controle que consiste em uma caixa de texto e um botão de redefinição. Designers visuais dão suporte avançado para a criação de controles compostos. Para criar um controle composto, derivam <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>. A classe base <xref:System.Windows.Forms.UserControl> fornece o roteamento de teclado para controles filho e permite que os controles filho funcionem como um grupo. Para obter mais informações, consulte [Desenvolvendo um controle composto do Windows Forms](developing-a-composite-windows-forms-control.md).  
  
- Estendendo um controle existente para personalizá-la ou aumentar sua funcionalidade.  
  
     Um botão cuja cor não pode ser alterado e um botão que tem uma propriedade adicional que controla quantas vezes ele foi clicado são exemplos de controles estendidos. Você pode personalizar qualquer controle do Windows Forms derivado dele e substituir ou adicionar propriedades, métodos e eventos.  
  
- Criando um controle que não combina ou estende os controles existentes.  
  
     Nesse cenário, derive o controle da classe base <xref:System.Windows.Forms.Control>. Você pode adicionar e substituir propriedades, métodos e eventos da classe base. Para começar, consulte [como: Desenvolver um controle de formulários do Windows simples](how-to-develop-a-simple-windows-forms-control.md).  
  
 A classe base para controles dos Windows Forms, <xref:System.Windows.Forms.Control>, fornece a estrutura necessária para a exibição visual em aplicativos baseados em Windows do lado do cliente. <xref:System.Windows.Forms.Control> Fornece um identificador de janela, manipula o roteamento de mensagens e fornece eventos de mouse e teclado, assim como muitos outro usuário eventos de interface. Ele fornece um layout avançado e tem as propriedades específicas para a exibição visual, como <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>e muitos outros. Além disso, ele fornece segurança, suporte a threading e interoperabilidade com controles ActiveX. Como grande parte da infraestrutura é fornecida pela classe base, é relativamente fácil desenvolver seus próprios controles do Windows Forms.  
  
## <a name="see-also"></a>Consulte também

- [Como: Desenvolver um controle de formulários do Windows simples](how-to-develop-a-simple-windows-forms-control.md)
- [Desenvolvendo um controle de composição dos Windows Forms](developing-a-composite-windows-forms-control.md)
- [Como: Criar um controle de formulários do Windows que mostre o progresso](how-to-create-a-windows-forms-control-that-shows-progress.md)
- [Variedades de controles personalizados](varieties-of-custom-controls.md)
