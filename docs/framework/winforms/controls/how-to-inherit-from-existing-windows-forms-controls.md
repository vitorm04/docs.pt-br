---
title: 'Como: Herdar de controles do Windows Forms existentes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0571bd6b169b94b1626bffb0d0793bbb22a93ba0
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015859"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Como: Herdar de controles do Windows Forms existentes

Se você quiser estender a funcionalidade de um controle existente, poderá criar um controle derivado de um controle existente por meio de herança. Ao herdar de um controle existente, você herda todas as funcionalidades e propriedades visuais desse controle. Por exemplo, se você estivesse criando um controle herdado de <xref:System.Windows.Forms.Button>, seu novo controle ficaria e agiria exatamente como um controle <xref:System.Windows.Forms.Button> padrão. Dessa forma, você poderia estender ou modificar a funcionalidade de seu novo controle por meio da implementação de métodos e propriedades personalizados. Em alguns controles, você também pode alterar a aparência visual do seu controle herdado substituindo <xref:System.Windows.Forms.Control.OnPaint%2A> seu método.

## <a name="to-create-an-inherited-control"></a>Criar um controle herdado

1. No Visual Studio, crie um novo projeto de **aplicativo Windows Forms** .

2. No menu **Projeto**, escolha **Adicionar Novo Item**.

     A caixa de diálogo **Adicionar Novo Item** é exibida.

3. Na caixa de diálogo **Adicionar Novo Item**, clique duas vezes em **Controle personalizado**.

     Um novo controle personalizado será adicionado ao projeto.

4. Se você estiver usando:

   - Visual Basic, na parte superior do **Gerenciador de soluções**, clique em **Mostrar todos os arquivos**. Expanda CustomControl1.vb e abra CustomControl1.Designer.vb no Editor de Código.
   - C#, abra CustomControl1.cs no editor de código.

6. Localize a declaração de classe que herda de <xref:System.Windows.Forms.Control>.

7. Altere a classe base para o controle do qual você deseja herdar.

     Por exemplo, se você quiser herdar de <xref:System.Windows.Forms.Button>, altere a declaração de classe para o seguinte:

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

8. Se você estiver usando Visual Basic, salve e feche CustomControl1.Designer.vb. Abra CustomControl1.vb no Editor de Código.

9. Implemente os métodos ou propriedades personalizados que o controle incorporará.

10. Se você quiser modificar a aparência gráfica do seu controle, substitua o <xref:System.Windows.Forms.Control.OnPaint%2A> método.

    > [!NOTE]
    > A <xref:System.Windows.Forms.Control.OnPaint%2A> substituição não permitirá que você modifique a aparência de todos os controles. Esses controles que têm toda a pintura feita pelo Windows (por exemplo, <xref:System.Windows.Forms.TextBox>) nunca chamam seu <xref:System.Windows.Forms.Control.OnPaint%2A> método e, portanto, nunca usarão o código personalizado. Consulte a documentação da ajuda para o controle específico que você deseja modificar para ver se o <xref:System.Windows.Forms.Control.OnPaint%2A> método está disponível. Para obter uma lista de todos os controles do Windows Forms, consulte [Controles a serem usados no Windows Forms](controls-to-use-on-windows-forms.md). Se um controle não estiver <xref:System.Windows.Forms.Control.OnPaint%2A> listado como um método de membro, você não poderá alterar sua aparência substituindo esse método. Para obter mais informações sobre pintura personalizada, consulte [Pintura e renderização de controle personalizado](custom-control-painting-and-rendering.md).

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

11. Salve e teste seu controle.

## <a name="see-also"></a>Consulte também

- [Variedades de controles personalizados](varieties-of-custom-controls.md)
- [Como: Herdar da classe de controle](how-to-inherit-from-the-control-class.md)
- [Como: Herdar da classe UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Como: Controles de autor para Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Solucionando problemas de manipuladores de eventos herdados no Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Passo a passo: Herdar de um controle de Windows Forms](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
