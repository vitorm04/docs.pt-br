---
title: Como herdar de controles dos Windows Forms existentes
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6049e5e0f2d79bab8ad90b6e63e91d4d4fa705ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Como herdar de controles dos Windows Forms existentes
Se você quiser estender a funcionalidade de um controle existente, poderá criar um controle derivado de um controle existente por meio de herança. Ao herdar de um controle existente, você herda todas as funcionalidades e propriedades visuais desse controle. Por exemplo, se você estivesse criando um controle que é herdado de <xref:System.Windows.Forms.Button>, o novo controle seria e funcionam exatamente como um padrão <xref:System.Windows.Forms.Button> controle. Dessa forma, você poderia estender ou modificar a funcionalidade de seu novo controle por meio da implementação de métodos e propriedades personalizados. Em alguns controles, você também pode alterar a aparência visual do seu controle herdado, substituindo seu <xref:System.Windows.Forms.Control.OnPaint%2A> método.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-an-inherited-control"></a>Criar um controle herdado  
  
1.  Para criar um novo projeto de **Aplicativo do Windows Forms**.  
  
2.  No menu **Projeto**, escolha **Adicionar Novo Item**.  
  
     A caixa de diálogo **Adicionar Novo Item** é exibida.  
  
3.  Na caixa de diálogo **Adicionar Novo Item**, clique duas vezes em **Controle personalizado**.  
  
     Um novo controle personalizado será adicionado ao projeto.  
  
4.  Se você usar o Visual Basic, no **Gerenciador de Soluções**, clique em **Mostrar todos os arquivos**. Expanda CustomControl1.vb e abra CustomControl1.Designer.vb no Editor de Código.  
  
5.  Se você estiver usando C#, abra CustomControl1.cs no Editor de Código.  
  
6.  Localize a declaração de classe que herda de <xref:System.Windows.Forms.Control>.  
  
7.  Altere a classe base para o controle do qual você deseja herdar.  
  
     Por exemplo, se você deseja herdar de <xref:System.Windows.Forms.Button>, altere a declaração de classe para o seguinte:  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8.  Se você estiver usando Visual Basic, salve e feche CustomControl1.Designer.vb. Abra CustomControl1.vb no Editor de Código.  
  
9. Implemente os métodos ou propriedades personalizados que o controle incorporará.  
  
10. Se você quiser modificar a aparência do gráfica de seu controle, substituir o <xref:System.Windows.Forms.Control.OnPaint%2A> método.  
  
    > [!NOTE]
    >  Substituindo <xref:System.Windows.Forms.Control.OnPaint%2A> não permitirá que você modifique a aparência de todos os controles. Esses controles que têm todas as sua pintura feita pelo Windows (por exemplo, <xref:System.Windows.Forms.TextBox>) nunca chamar seus <xref:System.Windows.Forms.Control.OnPaint%2A> método e, portanto, nunca use o código personalizado. Consulte a documentação de ajuda para o controle específico que você deseja modificar para ver se o <xref:System.Windows.Forms.Control.OnPaint%2A> método está disponível. Para obter uma lista de todos os controles do Windows Forms, consulte [Controles a serem usados no Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md). Se um controle não possui <xref:System.Windows.Forms.Control.OnPaint%2A> listado como um método de membro, você não pode alterar sua aparência substituir esse método. Para obter mais informações sobre pintura personalizada, consulte [Pintura e renderização de controle personalizado](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
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
 [Variedades de controles personalizados](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Como herdar da classe de controle](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [Como herdar da classe UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [Como Criar Controles para o Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Solucionando problemas de manipuladores de eventos herdados no Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [Passo a passo: herdando um controle dos Windows Forms com Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [Passo a passo: herdando um controle dos Windows Forms com Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
