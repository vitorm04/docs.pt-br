---
title: 'Passo a passo: mantendo um objeto no Visual Studio (C#)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: a544ce46-ee25-49da-afd4-457a3d59bf63
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b1a3fc377875ee25baa0718a25b5ac509822154
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-c"></a><span data-ttu-id="85987-102">Passo a passo: mantendo um objeto no Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="85987-102">Walkthrough: Persisting an Object in Visual Studio (C#)</span></span>
<span data-ttu-id="85987-103">Embora você possa definir as propriedades de um objeto para os valores padrão em tempo de design, qualquer valor inserido em tempo de execução será perdido quando o objeto for destruído.</span><span class="sxs-lookup"><span data-stu-id="85987-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="85987-104">Você pode usar a serialização para manter os dados de um objeto entre instâncias, o que permite armazenar valores e recuperá-los na próxima vez que o objeto for instanciado.</span><span class="sxs-lookup"><span data-stu-id="85987-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
 <span data-ttu-id="85987-105">Neste passo a passo, você criará um objeto `Loan` simples e manterá seus dados em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="85987-105">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="85987-106">Em seguida, você recuperará os dados do arquivo quando recriar o objeto.</span><span class="sxs-lookup"><span data-stu-id="85987-106">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="85987-107">Este exemplo criará um novo arquivo se o arquivo ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="85987-107">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="85987-108">Se um aplicativo precisar criar um arquivo, esse aplicativo precisará da permissão `Create` para a pasta.</span><span class="sxs-lookup"><span data-stu-id="85987-108">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="85987-109">Permissões são definidas usando listas de controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="85987-109">Permissions are set by using access control lists.</span></span> <span data-ttu-id="85987-110">Se o arquivo já existir, o aplicativo precisará somente da permissão `Write`, que é uma permissão menor.</span><span class="sxs-lookup"><span data-stu-id="85987-110">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="85987-111">Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder permissões `Read` a um único arquivo (em vez de permissões Create para uma pasta).</span><span class="sxs-lookup"><span data-stu-id="85987-111">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="85987-112">Além disso, é mais seguro gravar dados em pastas de usuário do que na pasta raiz ou na pasta Arquivos de Programas.</span><span class="sxs-lookup"><span data-stu-id="85987-112">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="85987-113">Este exemplo armazena dados em um arquivo de formato binário.</span><span class="sxs-lookup"><span data-stu-id="85987-113">This example stores data in a binary format file.</span></span> <span data-ttu-id="85987-114">Esses formatos não devem ser usados para dados confidenciais, como senhas ou informações de cartão de crédito.</span><span class="sxs-lookup"><span data-stu-id="85987-114">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85987-115">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="85987-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="85987-116">Para alterar as configurações, clique em **Importar e exportar configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="85987-116">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="85987-117">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="85987-117">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="85987-118">Criando o objeto Loan</span><span class="sxs-lookup"><span data-stu-id="85987-118">Creating the Loan Object</span></span>  
 <span data-ttu-id="85987-119">A primeira etapa é criar uma classe `Loan` e um aplicativo de teste que usa a classe.</span><span class="sxs-lookup"><span data-stu-id="85987-119">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="85987-120">Para criar a classe Loan</span><span class="sxs-lookup"><span data-stu-id="85987-120">To create the Loan class</span></span>  
  
1.  <span data-ttu-id="85987-121">Crie um novo projeto de Biblioteca de classes e denomine-o “LoanClass".</span><span class="sxs-lookup"><span data-stu-id="85987-121">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="85987-122">Para obter mais informações, consulte [Criando soluções e projetos](/visualstudio/ide/creating-solutions-and-projects).</span><span class="sxs-lookup"><span data-stu-id="85987-122">For more information, see [Creating Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2.  <span data-ttu-id="85987-123">No **Gerenciador de Soluções**, abra o menu de atalho para o arquivo Class1 e escolha **Renomear**.</span><span class="sxs-lookup"><span data-stu-id="85987-123">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="85987-124">Renomeie o arquivo como `Loan` e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="85987-124">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="85987-125">Renomear o arquivo também renomeará a classe para `Loan`.</span><span class="sxs-lookup"><span data-stu-id="85987-125">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3.  <span data-ttu-id="85987-126">Adicione os seguintes membros públicos à classe:</span><span class="sxs-lookup"><span data-stu-id="85987-126">Add the following public members to the class:</span></span>  
  
    ```csharp  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
        public double LoanAmount {get; set;}  
        public double InterestRate {get; set;}  
        public int Term {get; set;}  
  
        private string p_Customer;  
        public string Customer  
        {  
            get { return p_Customer; }  
            set   
            {  
                p_Customer = value;  
                PropertyChanged(this,  
                  new System.ComponentModel.PropertyChangedEventArgs("Customer"));  
            }  
        }  
  
        public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
  
        public Loan(double loanAmount,  
                    double interestRate,  
                    int term,  
                    string customer)  
        {  
            this.LoanAmount = loanAmount;  
            this.InterestRate = interestRate;  
            this.Term = term;  
            p_Customer = customer;  
        }  
    }  
    ```  
  
 <span data-ttu-id="85987-127">Você também precisará criar um aplicativo simples que usa a classe `Loan`.</span><span class="sxs-lookup"><span data-stu-id="85987-127">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="85987-128">Para criar um aplicativo de teste</span><span class="sxs-lookup"><span data-stu-id="85987-128">To create a test application</span></span>  
  
1.  <span data-ttu-id="85987-129">Para adicionar um projeto de Aplicativo do Windows Forms à sua solução, no menu **Arquivo**, escolha **Adicionar**, **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="85987-129">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="85987-130">Na caixa de diálogo **Adicionar Novo Projeto**, escolha **Aplicativo do Windows Forms** e insira `LoanApp` como o nome do projeto e clique **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="85987-130">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3.  <span data-ttu-id="85987-131">No **Gerenciador de Soluções**, escolha o projeto LoanApp.</span><span class="sxs-lookup"><span data-stu-id="85987-131">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4.  <span data-ttu-id="85987-132">No menu **Projeto**, escolha **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="85987-132">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="85987-133">No menu **Projeto**, escolha **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="85987-133">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6.  <span data-ttu-id="85987-134">Na caixa de diálogo **Adicionar Referência**, escolha a guia **Projetos** e escolha o projeto LoanClass.</span><span class="sxs-lookup"><span data-stu-id="85987-134">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7.  <span data-ttu-id="85987-135">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="85987-135">Click **OK** to close the dialog box.</span></span>  
  
8.  <span data-ttu-id="85987-136">No designer, adicione quatro controles <xref:System.Windows.Forms.TextBox> ao formulário.</span><span class="sxs-lookup"><span data-stu-id="85987-136">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="85987-137">No Editor de Códigos, adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="85987-137">In the Code Editor, add the following code:</span></span>  
  
    ```csharp  
    private LoanClass.Loan TestLoan = new LoanClass.Loan(10000.0, 0.075, 36, "Neil Black");  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        textBox1.Text = TestLoan.LoanAmount.ToString();  
        textBox2.Text = TestLoan.InterestRate.ToString();  
        textBox3.Text = TestLoan.Term.ToString();  
        textBox4.Text = TestLoan.Customer;  
    }  
    ```  
  
10. <span data-ttu-id="85987-138">Adicione um manipulador de eventos para o evento `PropertyChanged` do formulário usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="85987-138">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```csharp  
    private void CustomerPropertyChanged(object sender,   
        System.ComponentModel.PropertyChangedEventArgs e)  
    {  
        MessageBox.Show(e.PropertyName + " has been changed.");  
    }  
    ```  
  
 <span data-ttu-id="85987-139">Neste ponto, você pode compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="85987-139">At this point, you can build and run the application.</span></span> <span data-ttu-id="85987-140">Observe que os valores padrão da classe `Loan` aparecem nas caixas de texto.</span><span class="sxs-lookup"><span data-stu-id="85987-140">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="85987-141">Tente alterar o valor de taxa de juros de 7,5 para 7,1 e, em seguida, feche o aplicativo e execute-o novamente – o valor será revertido para o padrão de 7,5.</span><span class="sxs-lookup"><span data-stu-id="85987-141">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="85987-142">No mundo real, as taxas de juros mudam periodicamente, mas não necessariamente toda vez que o aplicativo for executado.</span><span class="sxs-lookup"><span data-stu-id="85987-142">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="85987-143">Em vez de fazer o usuário atualizar a taxa de juros sempre que o aplicativo for executado, é melhor preservar a taxa de juros mais recente entre instâncias do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="85987-143">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="85987-144">Na próxima etapa, você fará exatamente isso adicionando a serialização à classe Loan.</span><span class="sxs-lookup"><span data-stu-id="85987-144">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="85987-145">Usando a serialização para manter o objeto</span><span class="sxs-lookup"><span data-stu-id="85987-145">Using Serialization to Persist the Object</span></span>  
 <span data-ttu-id="85987-146">Para manter os valores da classe Loan, primeiro você deve marcar a classe com o atributo `Serializable`.</span><span class="sxs-lookup"><span data-stu-id="85987-146">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="85987-147">Para marcar uma classe como serializável</span><span class="sxs-lookup"><span data-stu-id="85987-147">To mark a class as serializable</span></span>  
  
-   <span data-ttu-id="85987-148">Altere a declaração da classe para a classe Loan da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="85987-148">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```csharp  
    [Serializable()]  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
    ```  
  
 <span data-ttu-id="85987-149">O atributo `Serializable` informa ao compilador que tudo na classe pode ser mantido em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="85987-149">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="85987-150">Como o evento `PropertyChanged` é manipulado por um objeto do Windows Forms, ele não pode ser serializado.</span><span class="sxs-lookup"><span data-stu-id="85987-150">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="85987-151">O atributo `NonSerialized` pode ser usado para marcar os membros da classe que não devem ser mantidos.</span><span class="sxs-lookup"><span data-stu-id="85987-151">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="85987-152">Para impedir que um membro seja serializado</span><span class="sxs-lookup"><span data-stu-id="85987-152">To prevent a member from being serialized</span></span>  
  
-   <span data-ttu-id="85987-153">Altere a declaração para o evento `PropertyChanged` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="85987-153">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```csharp  
    [field: NonSerialized()]  
    public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
    ```  
  
 <span data-ttu-id="85987-154">A etapa seguinte é adicionar o código de serialização ao aplicativo LoanApp.</span><span class="sxs-lookup"><span data-stu-id="85987-154">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="85987-155">Para serializar a classe e gravá-la em um arquivo, use os namespaces <xref:System.IO> e <xref:System.Xml.Serialization>.</span><span class="sxs-lookup"><span data-stu-id="85987-155">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="85987-156">Para evitar digitar os nomes totalmente qualificados, você pode adicionar referências às bibliotecas de classe necessárias.</span><span class="sxs-lookup"><span data-stu-id="85987-156">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="85987-157">Para adicionar referências a namespaces</span><span class="sxs-lookup"><span data-stu-id="85987-157">To add references to namespaces</span></span>  
  
-   <span data-ttu-id="85987-158">Adicione as seguintes instruções ao topo da classe `Form1`:</span><span class="sxs-lookup"><span data-stu-id="85987-158">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```csharp  
    using System.IO;  
    using System.Runtime.Serialization.Formatters.Binary;  
    ```  
  
     <span data-ttu-id="85987-159">Nesse caso, você está usando um formatador binário para salvar o objeto em um formato binário.</span><span class="sxs-lookup"><span data-stu-id="85987-159">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="85987-160">A próxima etapa é adicionar código para desserializar o objeto do arquivo quando o objeto for criado.</span><span class="sxs-lookup"><span data-stu-id="85987-160">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="85987-161">Para desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="85987-161">To deserialize an object</span></span>  
  
1.  <span data-ttu-id="85987-162">Adicione uma constante à classe para o nome do arquivo de dados serializado.</span><span class="sxs-lookup"><span data-stu-id="85987-162">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```csharp  
    const string FileName = @"..\..\SavedLoan.bin";  
    ```  
  
2.  <span data-ttu-id="85987-163">Modifique o código no procedimento do evento `Form1_Load` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="85987-163">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
    ```csharp  
    private LoanClass.Loan TestLoan = new LoanClass.Loan(10000.0, 0.075, 36, "Neil Black");  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        if (File.Exists(FileName))  
        {  
            Stream TestFileStream = File.OpenRead(FileName);  
            BinaryFormatter deserializer = new BinaryFormatter();  
            TestLoan = (LoanClass.Loan)deserializer.Deserialize(TestFileStream);  
            TestFileStream.Close();  
        }  
  
        TestLoan.PropertyChanged += this.CustomerPropertyChanged;  
  
        textBox1.Text = TestLoan.LoanAmount.ToString();  
        textBox2.Text = TestLoan.InterestRate.ToString();  
        textBox3.Text = TestLoan.Term.ToString();  
        textBox4.Text = TestLoan.Customer;  
    }  
    ```  
  
     <span data-ttu-id="85987-164">Observe que primeiro você deve verificar se o arquivo existe.</span><span class="sxs-lookup"><span data-stu-id="85987-164">Note that you first must check that the file exists.</span></span> <span data-ttu-id="85987-165">Se ele existir, crie uma classe <xref:System.IO.Stream> para ler o arquivo binário e uma classe <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> para converter o arquivo.</span><span class="sxs-lookup"><span data-stu-id="85987-165">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="85987-166">Você também precisa converter do tipo de fluxo para o tipo de objeto Loan.</span><span class="sxs-lookup"><span data-stu-id="85987-166">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="85987-167">Em seguida, você deve adicionar código para salvar os dados inseridos nas caixas de texto na classe `Loan` e, então, precisa serializar a classe em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="85987-167">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="85987-168">Para salvar os dados e serializar a classe</span><span class="sxs-lookup"><span data-stu-id="85987-168">To save the data and serialize the class</span></span>  
  
-   <span data-ttu-id="85987-169">Adicione o seguinte código ao procedimento do evento `Form1_FormClosing`:</span><span class="sxs-lookup"><span data-stu-id="85987-169">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
    ```csharp  
    private void Form1_FormClosing(object sender, FormClosingEventArgs e)  
    {  
        TestLoan.LoanAmount = Convert.ToDouble(textBox1.Text);  
        TestLoan.InterestRate = Convert.ToDouble(textBox2.Text);  
        TestLoan.Term = Convert.ToInt32(textBox3.Text);  
        TestLoan.Customer = textBox4.Text;  
  
        Stream TestFileStream = File.Create(FileName);  
        BinaryFormatter serializer = new BinaryFormatter();  
        serializer.Serialize(TestFileStream, TestLoan);  
        TestFileStream.Close();  
    }  
    ```  
  
 <span data-ttu-id="85987-170">Neste ponto, você pode compilar e executar o aplicativo novamente.</span><span class="sxs-lookup"><span data-stu-id="85987-170">At this point, you can again build and run the application.</span></span> <span data-ttu-id="85987-171">Inicialmente, os valores padrão aparecem nas caixas de texto.</span><span class="sxs-lookup"><span data-stu-id="85987-171">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="85987-172">Tente alterar os valores e digite um nome na quarta caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="85987-172">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="85987-173">Feche o aplicativo e execute-o novamente.</span><span class="sxs-lookup"><span data-stu-id="85987-173">Close the application and then run it again.</span></span> <span data-ttu-id="85987-174">Observe que agora os novos valores aparecem nas caixas de texto.</span><span class="sxs-lookup"><span data-stu-id="85987-174">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85987-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85987-175">See Also</span></span>  
 [<span data-ttu-id="85987-176">Serialização (C#)</span><span class="sxs-lookup"><span data-stu-id="85987-176">Serialization (C# )</span></span>](../../../../csharp/programming-guide/concepts/serialization/index.md)  
 [<span data-ttu-id="85987-177">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="85987-177">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
