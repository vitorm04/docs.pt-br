---
title: Crie um aplicativo do Windows Forms a partir da linha de comando
titleSuffix: ''
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
ms.openlocfilehash: 7bd3add526a6b60d628b05d46eca22ce407c36b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181983"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Como: Criar um aplicativo do Windows Forms a partir da linha de comando

Os procedimentos a seguir descrevem as etapas básicas que devem ser concluídas para criar e executar um aplicativo do Windows Forms na linha de comando. Há um suporte abrangente para esses procedimentos no Visual Studio.  Veja também [o Passo a Passo: Hospedando um controle de formulários do Windows no WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-create-the-form"></a>Criar o formulário  
  
1. Em um arquivo de código `Imports` `using` vazio, digite as seguintes declarações ou instruções:  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. Declare uma `Form1` classe nomeada que herda da classe Formulário:
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. Crie um construtor sem `Form1`parâmetros para .
  
     Mais código será adicionado ao construtor em um procedimento subsequente.
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. Adicione o método `Main` à classe.
  
    1. Aplique <xref:System.STAThreadAttribute> o método `Main` C# para especificar que o aplicativo Windows Forms é um apartamento com um único segmento. (O atributo não é necessário no Visual Basic, uma vez que o Windows forma aplicativos desenvolvidos com o Visual Basic usar um modelo de apartamento com um threaded por padrão.)  
  
    2. Chamada <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> para aplicar estilos do sistema operacional à sua aplicação.  
  
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
  
2. Na construtora, crie o botão <xref:System.Windows.Forms.Control.Size%2A>e <xref:System.Windows.Forms.Control.Location%2A> <xref:System.Windows.Forms.Control.Text%2A> defina suas propriedades e propriedades.  
  
3. Adicione o botão ao formulário.  
  
     O exemplo de código a seguir demonstra como declarar o controle do botão:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. Crie um método <xref:System.Windows.Forms.Control.Click> para lidar com o evento para o botão.  
  
5. No manipulador de eventos <xref:System.Windows.Forms.MessageBox> do clique, exiba um com a mensagem" Hello World".  
  
     O exemplo de código a seguir demonstra como lidar com o evento de clique do controle do botão:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. Associe o <xref:System.Windows.Forms.Control.Click> evento com o método que você criou.  
  
     O exemplo de código a seguir demonstra como associar o evento ao método.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. Compile e execute o aplicativo, conforme descrito no procedimento anterior.  
  
## <a name="example"></a>Exemplo  

O exemplo de código a seguir é o exemplo completo dos procedimentos anteriores:
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [Alterando a aparência dos Windows Forms](changing-the-appearance-of-windows-forms.md)
- [Aprimorando aplicativos do Windows Forms](./advanced/index.md)
- [Introdução ao Windows Forms](getting-started-with-windows-forms.md)
