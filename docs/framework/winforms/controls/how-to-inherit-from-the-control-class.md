---
title: 'Como: Herdar da classe Control'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 02c40e310778bd476742f62ee8b9d8598b084a53
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015850"
---
# <a name="how-to-inherit-from-the-control-class"></a>Como: Herdar da classe Control

Se você quiser criar um controle completamente personalizado para usar em um Windows Form, deverá herdar da <xref:System.Windows.Forms.Control> classe. Embora a <xref:System.Windows.Forms.Control> herança da classe exija que você execute mais planejamento e implementação, ela também fornece a maior variedade de opções. Ao herdar do <xref:System.Windows.Forms.Control>, você herda a funcionalidade muito básica que faz com que os controles funcionem. A funcionalidade inerente <xref:System.Windows.Forms.Control> à classe manipula a entrada do usuário através do teclado e do mouse, define os limites e o tamanho do controle, fornece um identificador do Windows e fornece segurança e manipulação de mensagens. Ela não incorpora nenhum pintura, que nesse caso é a renderização efetiva da interface gráfica do controle, nem incorpora qualquer funcionalidade de interação do usuário específica. Você deve fornecer todos esses aspectos por meio de código personalizado.

## <a name="to-create-a-custom-control"></a>Criar um controle personalizado

1. No Visual Studio, crie um novo **aplicativo do Windows** ou um projeto de **biblioteca de controle do Windows** .

2. No menu **Projeto**, escolha **Adicionar Classe**.

3. Na caixa de diálogo **Adicionar Novo Item**, clique em **Controle Personalizado**.

   Um novo controle personalizado será adicionado ao projeto.

4. Pressione **F7** para abrir o **Editor de código** para seu controle personalizado.

5. Localize o <xref:System.Windows.Forms.Control.OnPaint%2A> método, que estará vazio, exceto para uma chamada para o <xref:System.Windows.Forms.Control.OnPaint%2A> método da classe base.

6. Modifique o código para incorporar qualquer pintura personalizada desejada ao seu controle.

   Para obter informações sobre como escrever código para renderizar elementos gráficos para controles, consulte [Pintura e renderização de controle personalizado](custom-control-painting-and-rendering.md).

7. Implemente os métodos, propriedades ou eventos personalizados que o controle incorporará.

8. Salve e teste seu controle.

## <a name="see-also"></a>Consulte também

- [Variedades de controles personalizados](varieties-of-custom-controls.md)
- [Como: Herdar da classe UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Como: Herdar de controles de Windows Forms existentes](how-to-inherit-from-existing-windows-forms-controls.md)
- [Como: Controles de autor para Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Solucionando problemas de manipuladores de eventos herdados no Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Desenvolvendo controles dos Windows Forms em tempo de design](developing-windows-forms-controls-at-design-time.md)
