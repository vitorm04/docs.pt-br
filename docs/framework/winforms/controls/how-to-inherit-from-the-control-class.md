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
ms.openlocfilehash: 1a0eea1930699ed85fcf0eaf184ba0aabe398d73
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44031894"
---
# <a name="how-to-inherit-from-the-control-class"></a>Como herdar da classe de controle
Se você quiser criar um controle totalmente personalizado para usar em um formulário do Windows, você deve herdar o <xref:System.Windows.Forms.Control> classe. Ao mesmo tempo, herdando o <xref:System.Windows.Forms.Control> classe requer que você realizar mais planejamento e implementação, ele também fornece a maior gama de opções. Ao herdar de <xref:System.Windows.Forms.Control>, você herdará a funcionalidade muito básica que facilita o trabalho de controles. A funcionalidade inerente a <xref:System.Windows.Forms.Control> classe manipula a entrada do usuário por meio do teclado e mouse, define os limites e o tamanho do controle, fornece um identificador do windows e fornece a manipulação de mensagens e segurança. Ela não incorpora nenhum pintura, que nesse caso é a renderização efetiva da interface gráfica do controle, nem incorpora qualquer funcionalidade de interação do usuário específica. Você deve fornecer todos esses aspectos por meio de código personalizado.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-custom-control"></a>Criar um controle personalizado  
  
1.  Crie um novo projeto de **Aplicativos do Windows** ou **Biblioteca de Controle do Windows**.  
  
2.  No menu **Projeto**, escolha **Adicionar Classe**.  
  
3.  Na caixa de diálogo **Adicionar Novo Item**, clique em **Controle Personalizado**.  
  
     Um novo controle personalizado será adicionado ao projeto.  
  
4.  Pressione F7 para abrir o **Editor de código** para seu controle personalizado.  
  
5.  Localize o <xref:System.Windows.Forms.Control.OnPaint%2A> método, que estará vazio, exceto por uma chamada para o <xref:System.Windows.Forms.Control.OnPaint%2A> método da classe base.  
  
6.  Modifique o código para incorporar qualquer pintura personalizada desejada ao seu controle.  
  
     Para obter informações sobre como escrever código para renderizar elementos gráficos para controles, consulte [Pintura e renderização de controle personalizado](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
7.  Implemente os métodos, propriedades ou eventos personalizados que o controle incorporará.  
  
8.  Salve e teste seu controle.  
  
## <a name="see-also"></a>Consulte também  
 [Variedades de controles personalizados](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Como herdar da classe UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [Como herdar de controles dos Windows Forms existentes](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [Como Criar Controles para o Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Solucionando problemas de manipuladores de eventos herdados no Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [Desenvolvendo controles dos Windows Forms em tempo de design](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
