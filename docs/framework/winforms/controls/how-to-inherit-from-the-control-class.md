---
title: Como herdar da classe de controle
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7af7d1fe8f14c71dfc90836d84023b98feb44961
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458377"
---
# <a name="how-to-inherit-from-the-control-class"></a>Como herdar da classe de controle

Se você quiser criar um controle completamente personalizado para usar em um Windows Form, deve herdar da classe <xref:System.Windows.Forms.Control>. Embora a herança da classe <xref:System.Windows.Forms.Control> exija que você execute mais planejamento e implementação, ela também fornece a maior variedade de opções. Ao herdar de <xref:System.Windows.Forms.Control>, você herda a funcionalidade muito básica que faz com que os controles funcionem. A funcionalidade inerente à classe <xref:System.Windows.Forms.Control> manipula a entrada do usuário através do teclado e do mouse, define os limites e o tamanho do controle, fornece um identificador do Windows e fornece segurança e manipulação de mensagens. Ela não incorpora nenhum pintura, que nesse caso é a renderização efetiva da interface gráfica do controle, nem incorpora qualquer funcionalidade de interação do usuário específica. Você deve fornecer todos esses aspectos por meio de código personalizado.

## <a name="to-create-a-custom-control"></a>Criar um controle personalizado

1. No Visual Studio, crie um novo **aplicativo do Windows** ou um projeto de **biblioteca de controle do Windows** .

2. No menu **Projeto**, escolha **Adicionar Classe**.

3. Na caixa de diálogo **Adicionar Novo Item**, clique em **Controle Personalizado**.

   Um novo controle personalizado será adicionado ao projeto.

4. Pressione **F7** para abrir o **Editor de código** para seu controle personalizado.

5. Localize o método <xref:System.Windows.Forms.Control.OnPaint%2A>, que estará vazio, exceto para uma chamada para o método <xref:System.Windows.Forms.Control.OnPaint%2A> da classe base.

6. Modifique o código para incorporar qualquer pintura personalizada desejada ao seu controle.

   Para obter informações sobre como escrever código para renderizar elementos gráficos para controles, consulte [Pintura e renderização de controle personalizado](custom-control-painting-and-rendering.md).

7. Implemente os métodos, propriedades ou eventos personalizados que o controle incorporará.

8. Salve e teste seu controle.

## <a name="see-also"></a>Consulte também

- [Variedades de controles personalizados](varieties-of-custom-controls.md)
- [Como herdar da classe UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Como herdar de controles dos Windows Forms existentes](how-to-inherit-from-existing-windows-forms-controls.md)
- [Como Criar Controles para o Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Solucionando problemas de manipuladores de eventos herdados no Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Desenvolvendo controles dos Windows Forms em tempo de design](developing-windows-forms-controls-at-design-time.md)
