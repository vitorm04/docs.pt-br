---
title: Como criar um aplicativo Windows Forms na linha de comando
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
ms.openlocfilehash: af1548602ece8ea0f5720a836ec05648854e198f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127243"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Como criar um aplicativo Windows Forms na linha de comando

Os procedimentos a seguir descrevem as etapas básicas que devem ser concluídas para criar e executar um aplicativo do Windows Forms na linha de comando. Há um suporte abrangente para esses procedimentos no Visual Studio.  Consulte também [o passo a passos: hospedando um controle de Windows Forms no WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-create-the-form"></a>Criar o formulário  
  
1. Em um arquivo de código vazio, digite as seguintes `Imports` ou instruções de `using`:  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. Declare uma classe chamada `Form1` que herda da classe Form:
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. Crie um construtor sem parâmetros para `Form1`.
  
     Mais código será adicionado ao construtor em um procedimento subsequente.
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. Adicione o método `Main` à classe.
  
    1. Aplique o <xref:System.STAThreadAttribute> ao método C# `Main` para especificar seu aplicativo Windows Forms é um apartamento de thread único. (O atributo não é necessário em Visual Basic, já que os aplicativos do Windows Forms desenvolvidos com Visual Basic usam um modelo de apartamento de thread único por padrão.)  
  
    2. Chame <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> para aplicar estilos de sistema operacional ao seu aplicativo.  
  
    3. Crie uma instância do formulário e execute-o.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>Compilar e executar o aplicativo  
  
1. No prompt de comando do .NET Framework, navegue até o diretório em que a classe `Form1` foi criada.  
  
2. Compile o formulário.  
  
    - Se você estiver usando o C#, digite: `csc form1.cs`  
  
         `-or-`  
  
    - Se estiver usando Visual Basic, digite: `vbc form1.vb`  
  
3. No prompt de comando, digite: `Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>Adicionando um controle e manipulando um evento

As etapas do procedimento anterior demonstraram como criar um formulário básico do Windows Forms que compila e executa. O procedimento a seguir mostra como criar e adicionar um controle ao formulário e manipular um evento para o controle. Para obter mais informações sobre os controles que podem ser adicionados a formulários do Windows Forms, consulte [Controles do Windows Forms](./controls/index.md).
  
 Além de entender como criar aplicativos do Windows Forms, é necessário compreender a programação baseada em eventos e como tratar a entrada do usuário. Para obter mais informações, consulte [Criando Manipuladores de Eventos no Windows Forms](creating-event-handlers-in-windows-forms.md) e [Tratando a Entrada do Usuário](./controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Declarar um controle de botão e manipular o evento de clique  
  
1. Declare um controle de botão chamado `button1`.  
  
2. No construtor, crie o botão e defina suas propriedades <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> e <xref:System.Windows.Forms.Control.Text%2A>.  
  
3. Adicione o botão ao formulário.  
  
     O exemplo de código a seguir demonstra como declarar o controle Button:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. Crie um método para manipular o evento de <xref:System.Windows.Forms.Control.Click> para o botão.  
  
5. No manipulador de eventos de clique, exiba um <xref:System.Windows.Forms.MessageBox> com a mensagem "Olá, Mundo".  
  
     O exemplo de código a seguir demonstra como manipular o evento Click do controle Button:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. Associe o evento de <xref:System.Windows.Forms.Control.Click> com o método que você criou.  
  
     O exemplo de código a seguir demonstra como associar o evento ao método.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. Compile e execute o aplicativo, conforme descrito no procedimento anterior.  
  
## <a name="example"></a>Exemplo  
 
O exemplo de código a seguir é o exemplo completo dos procedimentos anteriores:
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [Alterando a aparência dos Windows Forms](changing-the-appearance-of-windows-forms.md)
- [Aprimorando aplicativos do Windows Forms](./advanced/index.md)
- [Introdução ao Windows Forms](getting-started-with-windows-forms.md)
