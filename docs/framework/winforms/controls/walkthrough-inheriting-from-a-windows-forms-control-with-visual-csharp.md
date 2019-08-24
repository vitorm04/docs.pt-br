---
title: 'Passo a passo: Herdando um controle do Windows Forms com Visual C#'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4a9a4b9bc15d2579837c3f4969a8d85293f10967
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015675"
---
# <a name="walkthrough-inherit-from-a-windows-forms-control-with-c"></a>Passo a passo: Herdar de um controle de Windows Forms com C\#

Com o C#Visual, você pode criar controles personalizados avançados por meio de *herança*. Com a herança, você é capaz de criar controles que mantêm todas as funcionalidades inerentes de controles padrão dos Windows Forms, mas também incorporam funcionalidades personalizadas. Neste passo a passo, você criará um controle herdado simples chamado `ValueButton`. Esse botão herdará a funcionalidade do controle de <xref:System.Windows.Forms.Button> Windows Forms padrão e apresentará uma propriedade personalizada chamada `ButtonValue`.

## <a name="create-the-project"></a>Criar o projeto

Quando cria um novo projeto, você especifica seu nome para definir o namespace raiz, o nome do assembly e o nome do projeto e para garantir que o componente padrão estará no namespace correto.

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>Para criar a biblioteca de controle ValueButtonLib e o controle ValueButton

1. No Visual Studio, crie um novo projeto de **biblioteca de controle Windows Forms** e nomeie-o **ValueButtonLib**.

     O nome do projeto, `ValueButtonLib`, também é atribuído ao namespace raiz por padrão. O namespace raiz é usado para qualificar os nomes dos componentes no assembly. Por exemplo, se dois assemblies fornecerem componentes chamados `ValueButton`, você poderá especificar o componente `ValueButton` usando `ValueButtonLib.ValueButton`. Para obter mais informações, consulte [Namespaces](../../../csharp/programming-guide/namespaces/index.md).

2. No **Gerenciador de Soluções**, clique com o botão direito do mouse em **UserControl1.cs** e escolha **Renomear** no menu de atalho. Altere o nome do arquivo para **ValueButton.cs**. Clique no botão **Sim** quando solicitado se desejar renomear todas as referências ao elemento de código '`UserControl1`'.

3. No **Gerenciador de Soluções**, clique com o botão direito do mouse em **ValueButton.cs** e selecione **Exibir Código**.

4. Localize a `class` linha de instrução `public partial class ValueButton`, e altere o tipo do <xref:System.Windows.Forms.UserControl> qual <xref:System.Windows.Forms.Button>esse controle herda. Isso permite que o controle herdado herde toda a funcionalidade <xref:System.Windows.Forms.Button> do controle.

5. No **Gerenciador de Soluções**, abra o nó **ValueButton.cs** para exibir o arquivo de código gerado pelo designer, **ValueButton.Designer.cs**. Abra esse arquivo no **Editor de Códigos**.

6. Localize o `InitializeComponent` método e remova a linha que atribui a <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> propriedade. Esta propriedade não existe no <xref:System.Windows.Forms.Button> controle.

7. No menu **Arquivo**, escolha **Salvar Tudo** para salvar o projeto.

    > [!NOTE]
    > Um designer visual não está mais disponível. Como o <xref:System.Windows.Forms.Button> controle faz sua própria pintura, você não pode modificar sua aparência no designer. Sua representação visual será exatamente igual à da classe da qual ela herda (ou seja, <xref:System.Windows.Forms.Button>), a menos que seja modificada no código. Você ainda pode adicionar componentes, que não têm uma interface do usuário, à superfície de design.

## <a name="add-a-property-to-your-inherited-control"></a>Adicionar uma propriedade ao controle herdado

Um uso possível dos controles herdados dos Windows Forms é a criação de controles que são idênticos em termos de aparência a controles padrão dos Windows Forms, mas que expõem propriedades personalizadas. Nesta seção, você adicionará uma propriedade chamada `ButtonValue` ao controle.

### <a name="to-add-the-value-property"></a>Para adicionar a propriedade de valor

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse em **ValueButton.cs** e, depois, clique em **Exibir Código** no menu de atalho.

2. Localize a instrução `class`. Cole o código a seguir imediatamente depois de `{`:

    ```csharp
    // Creates the private variable that will store the value of your
    // property.
    private int varValue;
    // Declares the property.
    public int ButtonValue
    {
       // Sets the method for retrieving the value of your property.
       get
       {
          return varValue;
       }
       // Sets the method for setting the value of your property.
       set
       {
          varValue = value;
       }
    }
    ```

     Esse código define os métodos segundo os quais a propriedade `ButtonValue` é armazenada e recuperada. A instrução `get` define o valor retornado como o valor que é armazenado na variável particular `varValue` e a instrução `set` define o valor da variável particular usando a palavra-chave `value`.

3. No menu **Arquivo**, escolha **Salvar Tudo** para salvar o projeto.

## <a name="test-the-control"></a>Testar o controle

Controles não são projetos autônomos; eles devem ser hospedados em um contêiner. Para testar seu controle, você precisa fornecer um projeto de teste em que ele será executado. Você também precisa tornar seu controle acessível para o projeto de teste compilando-o. Nesta seção, você compilará seu controle e o testará em um Windows Form.

### <a name="to-build-your-control"></a>Para compilar seu controle

No menu **Compilar**, clique em **Compilar Solução**. O build deve ser bem-sucedido, sem avisos ou erros do compilador.

### <a name="to-create-a-test-project"></a>Para criar um projeto de teste

1. No menu **Arquivo**, aponte para **Adicionar** e clique em **Novo Projeto** para abrir a caixa de diálogo **Adicionar Novo Projeto**.

2. Selecione o nó **Windows**, abaixo de **Visual C#** e clique em **Aplicativo dos Windows Forms**.

3. Na caixa **nome** , insira **teste**.

4. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Referências** de seu projeto de teste e selecione **Adicionar Referência** no menu de atalho para exibir a caixa de diálogo **Adicionar Referência**.

5. Clique na guia rotulada como **Projetos**. Seu projeto ValueButtonLib será listado em **nome do projeto**. Clique duas vezes no projeto para adicionar a referência ao projeto de teste.

6. No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Testar** e selecione **Compilar**.

### <a name="to-add-your-control-to-the-form"></a>Para adicionar o controle ao formulário

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Form1.cs** e selecione **Designer de Modo de Exibição** no menu de atalho.

2. Na **caixa de ferramentas**, selecione **componentes do ValueButtonLib**. Clique duas vezes em **ValueButton**.

     Um **ValueButton** aparece no formulário.

3. Clique com o botão direito do mouse em **ValueButton** e selecione **Propriedades** no menu de atalho.

4. Na janela **Propriedades**, examine as propriedades desse controle. Observe que eles são idênticos às propriedades expostas por um botão padrão, exceto pelo fato de que há uma propriedade adicional, ButtonValue.

5. Defina a Propriedade ButtonValue como **5**.

6. Na guia **todos os Windows Forms** da **caixa de ferramentas**, clique duas vezes em **rótulo** para <xref:System.Windows.Forms.Label> adicionar um controle ao formulário.

7. Reposicione o rótulo no centro do formulário.

8. Clique duas vezes em `valueButton1`.

     O **Editor de Códigos** é aberto no evento `valueButton1_Click`.

9. Insira a seguinte linha de código.

    ```csharp
    label1.Text = valueButton1.ButtonValue.ToString();
    ```

10. No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Teste** e escolha **Definir como Projeto de Inicialização** no menu de atalho.

11. No menu **Depuração**, selecione **Iniciar Depuração**.

     `Form1` é exibido.

12. Clique em `valueButton1`.

     O numeral "5" é exibido em `label1`, demonstrando que a propriedade `ButtonValue` de seu controle herdado foi passada para `label1` por meio do método `valueButton1_Click`. Portanto, seu controle `ValueButton` herda todas as funcionalidades do botão padrão dos Windows Forms, mas expõe uma propriedade adicional personalizada.

## <a name="see-also"></a>Consulte também

- [Como: Exibir um controle na caixa de diálogo escolher itens da Toolbox](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Passo a passo: Criando um controle composto com VisualC#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
