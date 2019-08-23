---
title: 'Como: Herdar da classe UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
ms.openlocfilehash: 77233517203989f188a2b3ddf436656bc8da82a6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966562"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>Como: Herdar da classe UserControl
Para combinar a funcionalidade de um ou mais controles do Windows Forms no modo personalizado, é possível criar um *controle de usuário*. Os controles de usuário combinam rápido desenvolvimento de controle, a funcionalidade padrão de controle do Windows Forms e a versatilidade de propriedades e métodos personalizados. Ao começar a criar um controle de usuário tomamos contato com um designer visível, sobre o qual é possível colocar controles padrão do Windows Forms. Esses controles mantêm todas suas funcionalidades inerentes, bem como a aparência e o comportamento (look and feel) dos controles padrão. No entanto, uma vez que esses controles são incorporados no controle de usuário, eles não estão mais disponíveis por meio de código. O controle de usuário faz sua própria pintura e também manipula toda a funcionalidade básica associada com controles.

## <a name="to-create-a-user-control"></a>Para criar um controle de usuário

1. Criar um novo projeto de **Biblioteca de Controle do Windows**.

     Um novo projeto é criado com um controle de usuário em branco.

2. Arraste os controles da aba **Windows Forms** da **Caixa de ferramentas** para o designer.

3. Esses controles devem ser posicionados e projetados como se deseja que eles apareçam no controle de usuário final. Se quiser permitir que os desenvolvedores acessem os controles constituintes, será preciso declará-los como públicos ou exibir seletivamente as propriedades do controle constituinte. Para obter detalhes, confira [Como: Expor propriedades de controles](how-to-expose-properties-of-constituent-controls.md)constituintes.

4. Implemente os métodos ou propriedades personalizados que o controle incorporará.

5. Pressione F5 para compilar o projeto e execute seu controle no **Contêiner de Teste de UserControl**. Para obter mais informações, confira [Como: Testar o comportamento de tempo de execução de um](how-to-test-the-run-time-behavior-of-a-usercontrol.md)UserControl.

## <a name="see-also"></a>Consulte também

- [Variedades de controles personalizados](varieties-of-custom-controls.md)
- [Como: Herdar da classe de controle](how-to-inherit-from-the-control-class.md)
- [Como: Herdar de controles de Windows Forms existentes](how-to-inherit-from-existing-windows-forms-controls.md)
- [Como: Controles de autor para Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Solucionando problemas de manipuladores de eventos herdados no Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Como: Testar o comportamento de tempo de execução de um UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
