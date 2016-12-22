---
title: "Passo a passo: Mantendo um objeto no Visual Studio (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "VB"
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Passo a passo: Mantendo um objeto no Visual Studio (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Embora você possa definir propriedades de um objeto com valores padrão em tempo de design, quaisquer valores inseridos em tempo de execução são perdidos quando o objeto é destruído. Você pode usar serialização para manter os dados de um objeto entre instâncias, que permite que você armazene valores e recuperá\-las na próxima vez que o objeto é instanciado.  
  
> [!NOTE]
>  No Visual Basic, para armazenar dados simples, como um nome ou número, você pode usar o `My.Settings` objeto. Para obter mais informações, consulte [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
 Neste passo a passo, você criará um simples `Loan` de objeto e manter seus dados em um arquivo. Em seguida, recuperará os dados do arquivo quando você recriar o objeto.  
  
> [!IMPORTANT]
>  Este exemplo cria um novo arquivo, se o arquivo ainda não existir. Se um aplicativo deve criar um arquivo, o aplicativo deve `Create` permissão para a pasta. As permissões são definidas usando listas de controle de acesso. Se o arquivo já existir, o aplicativo precisa apenas `Write` permissão, uma permissão menos. Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder `Read` permissões para um único arquivo \(em vez de criar permissões para uma pasta\). Além disso, é mais seguro gravar dados em pastas de usuário que a pasta raiz ou a pasta arquivos de programas.  
  
> [!IMPORTANT]
>  Este exemplo armazena dados em um binário. Esses formatos não devem ser usados para dados confidenciais, como senhas ou informações de cartão de crédito.  
  
> [!NOTE]
>  Caixas de diálogo e comandos de menu que você vê podem diferir daqueles descritos na Ajuda, dependendo de suas configurações ativas ou edição. Para alterar as configurações, clique em **Import and Export Settings** sobre o **ferramentas** menu. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Criando o objeto de empréstimo  
 A primeira etapa é criar um `Loan` classe e um aplicativo de teste que usa a classe.  
  
#### Para criar a classe de empréstimo  
  
1.  Criar um novo projeto de biblioteca de classes e nomeie\-a como "LoanClass". Para obter mais informações, consulte [Criando soluções e projetos](/visual-studio/ide/creating-solutions-and-projects).  
  
2.  Em **Solution Explorer**, abra o menu de atalho para o arquivo Class1 e escolha **Renomear**. Renomeie o arquivo como `Loan` e pressione ENTER. Renomear o arquivo também renomear a classe `Loan`.  
  
3.  Adicione os seguintes membros públicos na classe:  
  
    ```vb  
    Public Class Loan  
        Implements System.ComponentModel.INotifyPropertyChanged  
  
        Public Property LoanAmount As Double  
        Public Property InterestRate As Double  
        Public Property Term As Integer  
  
        Private p_Customer As String  
        Public Property Customer As String  
            Get  
                Return p_Customer  
            End Get  
            Set(ByVal value As String)  
                p_Customer = value  
                RaiseEvent PropertyChanged(Me,  
                  New System.ComponentModel.PropertyChangedEventArgs("Customer"))  
            End Set  
        End Property  
  
        Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
          Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
  
        Public Sub New(ByVal loanAmount As Double,  
                       ByVal interestRate As Double,  
                       ByVal term As Integer,  
                       ByVal customer As String)  
  
            Me.LoanAmount = loanAmount  
            Me.InterestRate = interestRate  
            Me.Term = term  
            p_Customer = customer  
        End Sub  
    End Class  
    ```  
  
 Você também terá que criar um aplicativo simples que usa o `Loan` classe.  
  
#### Para criar um aplicativo de teste  
  
1.  Para adicionar um projeto de aplicativo do Windows Forms para sua solução, no **arquivo** menu, escolha **Add**,**novo projeto**.  
  
2.  No **Adicionar novo projeto** caixa de diálogo, escolha **Windows Forms Application**, e digite `LoanApp` como o nome do projeto e, em seguida, clique **OK** para fechar a caixa de diálogo.  
  
3.  Em **Solution Explorer**, escolha o projeto LoanApp.  
  
4.  Sobre o **projeto** menu, escolha **Set as StartUp Project**.  
  
5.  Sobre o **projeto** menu, escolha **Adicionar referência**.  
  
6.  No **Adicionar referência** caixa de diálogo, escolha o **projetos** guia e, em seguida, escolha o projeto LoanClass.  
  
7.  Clique em **OK** para fechar a caixa de diálogo.  
  
8.  No designer, adicione quatro <xref:System.Windows.Forms.TextBox> controles ao formulário.  
  
9. No Editor de códigos, adicione o seguinte código:  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. Adicionar um manipulador de eventos para o `PropertyChanged` evento para o formulário usando o código a seguir:  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 Neste ponto, você pode compilar e executar o aplicativo. Observe que os valores padrão da `Loan` classe aparecem nas caixas de texto. Tente alterar o valor de taxa de juros de 7.5 para 7.1 e, em seguida, feche o aplicativo e executá\-la novamente, o valor será revertido para o padrão de 7.5.  
  
 No mundo real, taxas de juros alterar periodicamente, mas não necessariamente toda vez que o aplicativo é executado. Em vez de fazer com que o usuário atualizar a taxa de juros toda vez que o aplicativo é executado, é melhor preservar a taxa de juros mais recente entre instâncias do aplicativo. Na próxima etapa, você fará exatamente isso adicionando serialização à classe empréstimo.  
  
## Usando a serialização para manter o objeto  
 Para manter os valores para a classe de empréstimo, você deve primeiro marcar a classe com o `Serializable` atributo.  
  
#### Para marcar uma classe como serializável  
  
-   Altere a declaração de classe para a classe de empréstimo da seguinte maneira:  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 O `Serializable` atributo informa ao compilador que tudo na classe pode ser mantido em um arquivo. Porque o `PropertyChanged` evento é manipulado por um objeto de formulário do Windows, ele não pode ser serializado. O `NonSerialized` atributo pode ser usado para marcar os membros de classe que não devem ser persistentes.  
  
#### Para impedir que um membro que está sendo serializado  
  
-   Altere a declaração para o `PropertyChanged` evento da seguinte maneira:  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 A próxima etapa é adicionar o código de serialização para o aplicativo LoanApp. Para serializar a classe e gravá\-lo em um arquivo, você usará o <xref:System.IO> e <xref:System.Xml.Serialization> namespaces. Para evitar a digitação dos nomes totalmente qualificados, você pode adicionar referências a bibliotecas de classe necessária.  
  
#### Para adicionar referências aos namespaces  
  
-   Adicione as seguintes instruções na parte superior do `Form1` classe:  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     Nesse caso, você está usando um formatador binário para salvar o objeto em um formato binário.  
  
 A próxima etapa é adicionar código para desserializar o objeto do arquivo quando o objeto é criado.  
  
#### Para desserializar um objeto  
  
1.  Adicione uma constante para a classe para o nome do arquivo de dados serializados.  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2.  Modifique o código no `Form1_Load` procedimento de evento da seguinte maneira:  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        If File.Exists(FileName) Then  
            Dim TestFileStream As Stream = File.OpenRead(FileName)  
            Dim deserializer As New BinaryFormatter  
            TestLoan = CType(deserializer.Deserialize(TestFileStream), LoanClass.Loan)  
            TestFileStream.Close()  
        End If  
  
        AddHandler TestLoan.PropertyChanged, AddressOf Me.CustomerPropertyChanged  
  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
     Observe que você primeiro deve verificar se o arquivo existe. Se ele existir, crie um <xref:System.IO.Stream> classe para ler o arquivo binário e um <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> classe para converter o arquivo. Você também precisa converter do tipo de fluxo para o tipo de objeto de empréstimo.  
  
 Em seguida, você deve adicionar código para salvar os dados inseridos nas caixas de texto para o `Loan` classe e, em seguida, você precisa serializar a classe em um arquivo.  
  
#### Para salvar os dados e a classe  
  
-   Adicione o seguinte código para o `Form1_FormClosing` procedimento de evento:  
  
    ```vb  
    Private Sub Form1_FormClosing() Handles MyBase.FormClosing  
        TestLoan.LoanAmount = CDbl(TextBox1.Text)  
        TestLoan.InterestRate = CDbl(TextBox2.Text)  
        TestLoan.Term = CInt(TextBox3.Text)  
        TestLoan.Customer = TextBox4.Text  
  
        Dim TestFileStream As Stream = File.Create(FileName)  
        Dim serializer As New BinaryFormatter  
        serializer.Serialize(TestFileStream, TestLoan)  
        TestFileStream.Close()  
    End Sub  
    ```  
  
 Neste ponto, você pode novamente Compile e execute o aplicativo. Inicialmente, os valores padrão aparecem nas caixas de texto. Tente alterar os valores e digite um nome na quarta caixa de texto. Feche o aplicativo e execute\-o novamente. Observe que os novos valores agora aparecem nas caixas de texto.  
  
## Consulte também  
 [Serialização \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)   
 [Guia de programação do Visual Basic](../../../../visual-basic/programming-guide/index.md)