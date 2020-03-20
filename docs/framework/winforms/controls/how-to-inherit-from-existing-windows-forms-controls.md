---
title: Herdar de controles existentes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b0e0053816efde349c7e4d13d03bef5f8801c667
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849374"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Como herdar de controles dos Windows Forms existentes

Se você quiser estender a funcionalidade de um controle existente, poderá criar um controle derivado de um controle existente por meio de herança. Ao herdar de um controle existente, você herda todas as funcionalidades e propriedades visuais desse controle. Por exemplo, se você estivesse criando <xref:System.Windows.Forms.Button>um controle que herdou, seu <xref:System.Windows.Forms.Button> novo controle pareceria e agiria exatamente como um controle padrão. Dessa forma, você poderia estender ou modificar a funcionalidade de seu novo controle por meio da implementação de métodos e propriedades personalizados. Em alguns controles, você também pode alterar a aparência visual <xref:System.Windows.Forms.Control.OnPaint%2A> do seu controle herdado, substituindo seu método.

## <a name="to-create-an-inherited-control"></a>Criar um controle herdado

1. No Visual Studio, crie um novo projeto **de aplicativo de formulários do Windows.**

1. No menu **Projeto**, escolha **Adicionar Novo Item**.

    A caixa de diálogo **Adicionar Novo Item** aparecerá.

1. Na caixa de diálogo **Adicionar Novo Item**, clique duas vezes em **Controle personalizado**.

    Um novo controle personalizado será adicionado ao projeto.

1. Se você estiver usando:

    - Visual Basic, na parte superior do **Solution Explorer,** clique em **Mostrar todos os arquivos**. Expanda CustomControl1.vb e abra CustomControl1.Designer.vb no Editor de Código.
    - C#, abra CustomControl1.cs no Editor de Códigos.

1. Localize a declaração de <xref:System.Windows.Forms.Control>classe, que herda de .

1. Altere a classe base para o controle do qual você deseja herdar.

     Por exemplo, se você <xref:System.Windows.Forms.Button>quiser herdar, altere a declaração de classe para o seguinte:

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. Se você estiver usando Visual Basic, salve e feche CustomControl1.Designer.vb. Abra CustomControl1.vb no Editor de Código.

1. Implemente os métodos ou propriedades personalizados que o controle incorporará.

1. Se você quiser modificar a aparência gráfica do <xref:System.Windows.Forms.Control.OnPaint%2A> seu controle, anule o método.

    > [!NOTE]
    > A <xref:System.Windows.Forms.Control.OnPaint%2A> substituição não permitirá que você modifique a aparência de todos os controles. Esses controles que têm toda a sua pintura <xref:System.Windows.Forms.TextBox>feita pelo <xref:System.Windows.Forms.Control.OnPaint%2A> Windows (por exemplo, ) nunca chamam seu método, e, portanto, nunca usarão o código personalizado. Consulte a documentação de Ajuda para o controle <xref:System.Windows.Forms.Control.OnPaint%2A> específico que deseja modificar para ver se o método está disponível. Para obter uma lista de todos os controles do Windows Forms, consulte [Controles a serem usados no Windows Forms](controls-to-use-on-windows-forms.md). Se um controle <xref:System.Windows.Forms.Control.OnPaint%2A> não tiver listado como um método de membro, você não poderá alterar sua aparência substituindo este método. Para obter mais informações sobre pintura personalizada, consulte [Pintura e renderização de controle personalizado](custom-control-painting-and-rendering.md).

    ```vb
    Protected Overrides Sub OnPaint(ByVal e As _
       System.Windows.Forms.PaintEventArgs)
       MyBase.OnPaint(e)
       ' Insert code to do custom painting.
       ' If you want to completely change the appearance of your control,
       ' do not call MyBase.OnPaint(e).
    End Sub
    ```

    ```csharp
    protected override void OnPaint(PaintEventArgs pe)
    {
       base.OnPaint(pe);
       // Insert code to do custom painting.
       // If you want to completely change the appearance of your control,
       // do not call base.OnPaint(pe).
    }
    ```

1. Salve e teste seu controle.

## <a name="see-also"></a>Confira também

- [Variedades de Controles Personalizados](varieties-of-custom-controls.md)
- [Como herdar da classe de controle](how-to-inherit-from-the-control-class.md)
- [Como herdar da classe UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Como Criar Controles para o Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Solucionando problemas de manipuladores de eventos herdados no Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Passo a passo: Herdando de um controle de formulários do Windows](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
