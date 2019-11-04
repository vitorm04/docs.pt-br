---
title: Como herdar de controles dos Windows Forms existentes
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
ms.openlocfilehash: 063f5bb87b6348ee83573cf1506c9fabdaf651ee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460570"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Como herdar de controles dos Windows Forms existentes

Se você quiser estender a funcionalidade de um controle existente, poderá criar um controle derivado de um controle existente por meio de herança. Ao herdar de um controle existente, você herda todas as funcionalidades e propriedades visuais desse controle. Por exemplo, se você estivesse criando um controle herdado de <xref:System.Windows.Forms.Button>, seu novo controle ficaria e agiria exatamente como um controle de <xref:System.Windows.Forms.Button> padrão. Dessa forma, você poderia estender ou modificar a funcionalidade de seu novo controle por meio da implementação de métodos e propriedades personalizados. Em alguns controles, você também pode alterar a aparência visual do seu controle herdado substituindo seu método <xref:System.Windows.Forms.Control.OnPaint%2A>.

## <a name="to-create-an-inherited-control"></a>Criar um controle herdado

1. No Visual Studio, crie um novo projeto de **aplicativo Windows Forms** .

1. No menu **Projeto**, escolha **Adicionar Novo Item**.

    A caixa de diálogo **Adicionar Novo Item** é exibida.

1. Na caixa de diálogo **Adicionar Novo Item**, clique duas vezes em **Controle personalizado**.

    Um novo controle personalizado será adicionado ao projeto.

1. Se você estiver usando:

    - Visual Basic, na parte superior do **Gerenciador de soluções**, clique em **Mostrar todos os arquivos**. Expanda CustomControl1.vb e abra CustomControl1.Designer.vb no Editor de Código.
    - C#, abra CustomControl1.cs no editor de código.

1. Localize a declaração de classe, que herda de <xref:System.Windows.Forms.Control>.

1. Altere a classe base para o controle do qual você deseja herdar.

     Por exemplo, se você quiser herdar de <xref:System.Windows.Forms.Button>, altere a declaração de classe para o seguinte:

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. Se você estiver usando Visual Basic, salve e feche CustomControl1.Designer.vb. Abra CustomControl1.vb no Editor de Código.

1. Implemente os métodos ou propriedades personalizados que o controle incorporará.

1. Se você quiser modificar a aparência gráfica do seu controle, substitua o método <xref:System.Windows.Forms.Control.OnPaint%2A>.

    > [!NOTE]
    > A substituição de <xref:System.Windows.Forms.Control.OnPaint%2A> não permitirá que você modifique a aparência de todos os controles. Esses controles que têm toda a pintura feita pelo Windows (por exemplo, <xref:System.Windows.Forms.TextBox>) nunca chamam o método <xref:System.Windows.Forms.Control.OnPaint%2A> e, portanto, nunca usarão o código personalizado. Consulte a documentação da ajuda para o controle específico que você deseja modificar para ver se o método de <xref:System.Windows.Forms.Control.OnPaint%2A> está disponível. Para obter uma lista de todos os controles do Windows Forms, consulte [Controles a serem usados no Windows Forms](controls-to-use-on-windows-forms.md). Se um controle não tiver <xref:System.Windows.Forms.Control.OnPaint%2A> listado como um método de membro, você não poderá alterar sua aparência substituindo esse método. Para obter mais informações sobre pintura personalizada, consulte [Pintura e renderização de controle personalizado](custom-control-painting-and-rendering.md).

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

## <a name="see-also"></a>Consulte também

- [Variedades de controles personalizados](varieties-of-custom-controls.md)
- [Como herdar da classe de controle](how-to-inherit-from-the-control-class.md)
- [Como herdar da classe UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Como Criar Controles para o Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Solucionando problemas de manipuladores de eventos herdados no Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Walkthrough: herdar de um controle de Windows Forms](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
