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
ms.openlocfilehash: 788addee7c024577d029626da4aeb86d0ca9076a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941148"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Como: Herdar de controles do Windows Forms existentes
Se você quiser estender a funcionalidade de um controle existente, poderá criar um controle derivado de um controle existente por meio de herança. Ao herdar de um controle existente, você herda todas as funcionalidades e propriedades visuais desse controle. Por exemplo, se você estivesse criando um controle herdado de <xref:System.Windows.Forms.Button>, o novo controle seria a aparência e funcionam exatamente como um padrão <xref:System.Windows.Forms.Button> controle. Dessa forma, você poderia estender ou modificar a funcionalidade de seu novo controle por meio da implementação de métodos e propriedades personalizados. Em alguns controles, você também pode alterar a aparência visual do controle herdado substituindo seu <xref:System.Windows.Forms.Control.OnPaint%2A> método.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-an-inherited-control"></a>Criar um controle herdado  
  
1. Para criar um novo projeto de **Aplicativo do Windows Forms**.  
  
2. No menu **Projeto**, escolha **Adicionar Novo Item**.  
  
     A caixa de diálogo **Adicionar Novo Item** é exibida.  
  
3. Na caixa de diálogo **Adicionar Novo Item**, clique duas vezes em **Controle personalizado**.  
  
     Um novo controle personalizado será adicionado ao projeto.  
  
4. Se você usar o Visual Basic, no **Gerenciador de Soluções**, clique em **Mostrar todos os arquivos**. Expanda CustomControl1.vb e abra CustomControl1.Designer.vb no Editor de Código.  
  
5. Se você estiver usando C#, abra CustomControl1.cs no Editor de Código.  
  
6. Localize a declaração de classe que herda de <xref:System.Windows.Forms.Control>.  
  
7. Altere a classe base para o controle do qual você deseja herdar.  
  
     Por exemplo, se você deseja herdar de <xref:System.Windows.Forms.Button>, altere a declaração de classe para o seguinte:  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8. Se você estiver usando Visual Basic, salve e feche CustomControl1.Designer.vb. Abra CustomControl1.vb no Editor de Código.  
  
9. Implemente os métodos ou propriedades personalizados que o controle incorporará.  
  
10. Se você quiser modificar a aparência gráfica do seu controle, substituir o <xref:System.Windows.Forms.Control.OnPaint%2A> método.  
  
    > [!NOTE]
    >  Substituindo <xref:System.Windows.Forms.Control.OnPaint%2A> não permitirá que você modificar a aparência de todos os controles. Os controles cuja pintura é feita pelo Windows (por exemplo, <xref:System.Windows.Forms.TextBox>) nunca chama seus <xref:System.Windows.Forms.Control.OnPaint%2A> método e, portanto, nunca usarão o código personalizado. Consulte a documentação de ajuda para o controle específico que você deseja modificar para ver se o <xref:System.Windows.Forms.Control.OnPaint%2A> método está disponível. Para obter uma lista de todos os controles do Windows Forms, consulte [Controles a serem usados no Windows Forms](controls-to-use-on-windows-forms.md). Se não tiver um controle <xref:System.Windows.Forms.Control.OnPaint%2A> listado como um método membro, você não pode alterar sua aparência substituindo esse método. Para obter mais informações sobre pintura personalizada, consulte [Pintura e renderização de controle personalizado](custom-control-painting-and-rendering.md).  
  
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
- [Como: Criar controles para Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Solucionando problemas de manipuladores de eventos herdados no Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Passo a passo: Herdando um controle de formulários do Windows com o Visual Basic](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [Passo a passo: Herdando um controle de formulários do Windows com VisualC#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
