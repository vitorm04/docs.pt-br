---
title: 'Instruções passo a passo: herdando um controle dos Windows Forms com Visual Basic'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 342ab60d4c3481d2154293fab9fb1254f937a934
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a>Instruções passo a passo: herdando um controle dos Windows Forms com Visual Basic
Com o Visual Basic, você pode criar controles personalizados eficientes por meio de *herança*. Com a herança, você é capaz de criar controles que mantêm todas as funcionalidades inerentes de controles padrão dos Windows Forms, mas também incorporam funcionalidades personalizadas. Neste passo a passo, você criará um controle herdado simples chamado `ValueButton`. Esse botão herdará a funcionalidade de formulários do Windows padrão <xref:System.Windows.Forms.Button> controlar e expõe uma propriedade personalizada chamada `ButtonValue`.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 Quando cria um novo projeto, você especifica seu nome para definir o namespace raiz, o nome do assembly e o nome do projeto e para garantir que o componente padrão estará no namespace correto.  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>Para criar a biblioteca de controle ValueButtonLib e o controle ValueButton  
  
1.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto** para abrir a caixa de diálogo **Novo Projeto**.  
  
2.  Selecione o **biblioteca de controle do Windows Forms** modelo de projeto da lista de projetos do Visual Basic e o tipo `ValueButtonLib` no **nome** caixa.  
  
     O nome do projeto, `ValueButtonLib`, também é atribuído ao namespace raiz por padrão. O namespace raiz é usado para qualificar os nomes dos componentes no assembly. Por exemplo, se dois assemblies fornecerem componentes chamados `ValueButton`, você poderá especificar o componente `ValueButton` usando `ValueButtonLib.ValueButton`. Para obter mais informações, consulte [Namespaces no Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).  
  
3.  No **Gerenciador de Soluções**, clique com o botão direito do mouse em **UserControl1.vb** e escolha **Renomear** no menu de atalho. Altere o nome de arquivo para `ValueButton.vb`. Clique no botão **Sim** quando for solicitado se quiser renomear todas as referências ao elemento de código “UserControl1”.  
  
4.  Em **Gerenciador de Soluções**, clique no botão **Mostrar Todos os Arquivos**.  
  
5.  Abra o nó **ValueButton.vb** para exibir o arquivo de código gerado pelo designer, **ValueButton.Designer.vb**. Abra esse arquivo no **Editor de Códigos**.  
  
6.  Localize o `Class` instrução, `Partial Public Class ValueButton`e alterar o tipo da qual este controle herda do <xref:System.Windows.Forms.UserControl> para <xref:System.Windows.Forms.Button>. Isso permite que o controle herdado herdar toda a funcionalidade do <xref:System.Windows.Forms.Button> controle.  
  
7.  Localize o `InitializeComponent` método e remova a linha que atribui o <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> propriedade. Essa propriedade não existe no <xref:System.Windows.Forms.Button> controle.  
  
8.  No menu **Arquivo**, escolha **Salvar Tudo** para salvar o projeto.  
  
     Observe que um designer visual não está mais disponível. Porque o <xref:System.Windows.Forms.Button> controle faz sua própria pintura, você não é possível modificar sua aparência no designer. Sua representação visual será exatamente o mesmo que ela herda da classe (ou seja, <xref:System.Windows.Forms.Button>), a menos que modificado no código.  
  
> [!NOTE]
>  Você ainda pode adicionar componentes, que não têm uma interface do usuário, à superfície de design.  
  
## <a name="adding-a-property-to-your-inherited-control"></a>Adicionando uma propriedade ao controle herdado  
 Um uso possível dos controles herdados dos Windows Forms é a criação de controles que são idênticos em termos de aparência e comportamento a controles padrão dos Windows Forms, mas que expõem propriedades personalizadas. Nesta seção, você adicionará uma propriedade chamada `ButtonValue` ao controle.  
  
#### <a name="to-add-the-value-property"></a>Para adicionar a propriedade de valor  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse em **ValueButton.vb** e, depois, clique em **Exibir Código** no menu de atalho.  
  
2.  Localize a instrução `Public Class ValueButton`. Logo abaixo dessa instrução, digite o código a seguir:  
  
    ```vb  
    ' Creates the private variable that will store the value of your   
    ' property.  
    Private varValue as integer  
    ' Declares the property.  
    Property ButtonValue() as Integer  
    ' Sets the method for retrieving the value of your property.  
       Get  
          Return varValue  
       End Get  
    ' Sets the method for setting the value of your property.  
       Set(ByVal Value as Integer)  
          varValue = Value  
       End Set  
    End Property  
    ```  
  
     Esse código define os métodos segundo os quais a propriedade `ButtonValue` é armazenada e recuperada. A instrução `Get` define o valor retornado como o valor que é armazenado na variável particular `varValue` e a instrução `Set` define o valor da variável particular usando a palavra-chave `Value`.  
  
3.  No menu **Arquivo**, escolha **Salvar Tudo** para salvar o projeto.  
  
## <a name="testing-your-control"></a>Testando seu controle  
 Controles não são projetos autônomos; eles devem ser hospedados em um contêiner. Para testar seu controle, você precisa fornecer um projeto de teste em que ele será executado. Você também precisa tornar seu controle acessível para o projeto de teste compilando-o. Nesta seção, você compilará seu controle e o testará em um Windows Form.  
  
#### <a name="to-build-your-control"></a>Para compilar seu controle  
  
1.  No menu **Compilar**, clique em **Compilar Solução**.  
  
     O build deve ser bem-sucedido, sem avisos ou erros do compilador.  
  
#### <a name="to-create-a-test-project"></a>Para criar um projeto de teste  
  
1.  No menu **Arquivo**, aponte para **Adicionar** e clique em **Novo Projeto** para abrir a caixa de diálogo **Adicionar Novo Projeto**.  
  
2.  Selecione o nó de projetos do Visual Basic e, em seguida, clique em **aplicativo do Windows Forms**.  
  
3.  Na caixa **Nome**, digite `Test`.  
  
4.  Em **Gerenciador de Soluções**, clique no botão **Mostrar Todos os Arquivos**.  
  
5.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Referências** de seu projeto de teste e selecione **Adicionar Referência** no menu de atalho para exibir a caixa de diálogo **Adicionar Referência**.  
  
6.  Clique na guia **Projetos**.  
  
7.  Clique na guia rotulada como **Projetos**. O projeto `ValueButtonLib` estará listado em **Nome do Projeto**. Clique duas vezes no projeto para adicionar a referência ao projeto de teste.  
  
8.  No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Testar** e selecione **Compilar**.  
  
#### <a name="to-add-your-control-to-the-form"></a>Para adicionar o controle ao formulário  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Form1.vb** e selecione **Designer de Modo de Exibição** no menu de atalho.  
  
2.  Na **Caixa de Ferramentas**, clique em **Componentes de ValueButtonLib**. Clique duas vezes em **ValueButton**.  
  
     Um **ValueButton** aparece no formulário.  
  
3.  Clique com o botão direito do mouse em **ValueButton** e selecione **Propriedades** no menu de atalho.  
  
4.  Na janela **Propriedades**, examine as propriedades desse controle. Observe que elas são idênticas às propriedades expostas por um botão padrão, exceto pelo fato de que há uma propriedade adicional, `ButtonValue`.  
  
5.  Defina a propriedade `ButtonValue` como `5`.  
  
6.  No **todos os Windows Forms** guia do **caixa de ferramentas**, clique duas vezes em **rótulo** para adicionar um <xref:System.Windows.Forms.Label> a seu formulário.  
  
7.  Reposicione o rótulo no centro do formulário.  
  
8.  Clique duas vezes em `ValueButton1`.  
  
     O **Editor de Códigos** é aberto no evento `ValueButton1_Click`.  
  
9. Digite a seguinte linha de código.  
  
    ```vb  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Teste** e escolha **Definir como Projeto de Inicialização** no menu de atalho.  
  
11. No menu **Depuração**, selecione **Iniciar Depuração**.  
  
     `Form1` é exibido.  
  
12. Clique em `Valuebutton1`.  
  
     O numeral "5" é exibido em `Label1`, demonstrando que a propriedade `ButtonValue` de seu controle herdado foi passada para `Label1` por meio do método `ValueButton1_Click`. Portanto, seu controle `ValueButton` herda todas as funcionalidades do botão padrão dos Windows Forms, mas expõe uma propriedade adicional personalizada.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: criando um controle de composição com o Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [Como exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Noções básicas de herança (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Instruções passo a passo para criação de componentes](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
