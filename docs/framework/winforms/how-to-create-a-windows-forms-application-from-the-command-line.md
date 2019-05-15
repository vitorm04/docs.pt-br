---
title: 'Como: Criar um aplicativo do Windows Forms a partir da linha de comando'
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 72195dd49c163b26a5bcfa739768718f2a32f346
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588983"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Como: Criar um aplicativo do Windows Forms a partir da linha de comando
Os procedimentos a seguir descrevem as etapas básicas que devem ser concluídas para criar e executar um aplicativo do Windows Forms na linha de comando. Há um suporte abrangente para esses procedimentos no Visual Studio.  Consulte também [passo a passo: Controle hospeda um Windows Forms no WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-create-the-form"></a>Criar o formulário  
  
1. Em um arquivo de código vazio, digite as seguintes instruções de importação ou uso:  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. Declare uma classe chamada `Form1` que herda da classe Form.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. Crie um construtor padrão para `Form1`.  
  
     Mais código será adicionado ao construtor em um procedimento subsequente.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. Adicione o método `Main` à classe.  
  
    1. Aplicar a <xref:System.STAThreadAttribute> para o c# `Main` método para especificar o aplicativo Windows Forms é um single-threaded apartment. (O atributo não é necessário no Visual Basic, uma vez que o Windows forms aplicativos desenvolvidos com o uso do Visual Basic um modelo de single-threaded apartment por padrão.)  
  
    2. Chamar <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> para aplicar estilos de sistema operacional para seu aplicativo.  
  
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
  
## <a name="adding-a-control-and-handling-an-event"></a>Adicionando um Controle e Manipulando um Evento  
 As etapas do procedimento anterior demonstraram como criar um formulário básico do Windows Forms que compila e executa. O procedimento a seguir mostra como criar e adicionar um controle ao formulário e manipular um evento para o controle. Para obter mais informações sobre os controles que podem ser adicionados a formulários do Windows Forms, consulte [Controles do Windows Forms](./controls/index.md).  
  
 Além de entender como criar aplicativos do Windows Forms, é necessário compreender a programação baseada em eventos e como tratar a entrada do usuário. Para obter mais informações, consulte [Criando Manipuladores de Eventos no Windows Forms](creating-event-handlers-in-windows-forms.md) e [Tratando a Entrada do Usuário](./controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Declarar um controle de botão e manipular o evento de clique  
  
1. Declare um controle de botão chamado `button1`.  
  
2. No construtor, crie o botão e defina suas <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> e <xref:System.Windows.Forms.Control.Text%2A> propriedades.  
  
3. Adicione o botão ao formulário.  
  
     O exemplo de código a seguir demonstra como declarar o controle de botão.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. Crie um método para manipular o <xref:System.Windows.Forms.Control.Click> evento do botão.  
  
5. No manipulador de eventos de clique, exiba um <xref:System.Windows.Forms.MessageBox> com a mensagem "Hello World".  
  
     O exemplo de código a seguir demonstra como manipular o evento de clique do controle de botão.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. Associar o <xref:System.Windows.Forms.Control.Click> eventos com o método que você criou.  
  
     O exemplo de código a seguir demonstra como associar o evento ao método.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. Compile e execute o aplicativo, conforme descrito no procedimento anterior.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir é o exemplo completo dos procedimentos anteriores.  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [Alterando a aparência dos Windows Forms](changing-the-appearance-of-windows-forms.md)
- [Aprimorando aplicativos do Windows Forms](./advanced/index.md)
- [Guia de introdução ao Windows Forms](getting-started-with-windows-forms.md)
