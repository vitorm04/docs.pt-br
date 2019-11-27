---
title: 'Instruções passo a passo: implementando a herança com objetos COM'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: 209e1005b9f944bf4883e8406031fb17d4d60df1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347995"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>Instruções passo a passo: implementando a herança com objetos COM (Visual Basic)

Você pode derivar classes de Visual Basic de `Public` classes em objetos COM, mesmo aquelas criadas em versões anteriores do Visual Basic. As propriedades e os métodos de classes herdadas dos objetos COM podem ser substituídos ou sobrecarregados, assim como as propriedades e os métodos de qualquer outra classe base podem ser substituídos ou sobrecarregados. A herança de objetos COM é útil quando você tem uma biblioteca de classes existente que não deseja recompilar.

O procedimento a seguir mostra como usar Visual Basic 6,0 para criar um objeto COM que contém uma classe e, em seguida, usá-lo como uma classe base.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>Para compilar o objeto COM que é usado neste tutorial

1. No Visual Basic 6,0, abra um novo projeto de DLL do ActiveX. Um projeto chamado `Project1` é criado. Ele tem uma classe chamada `Class1`.

2. No **Gerenciador de projetos**, clique com o botão direito do mouse em **Projeto1**e clique em **Propriedades de Projeto1**. A caixa de diálogo **Propriedades do projeto** é exibida.

3. Na guia **geral** da caixa de diálogo **Propriedades do projeto** , altere o nome do projeto digitando `ComObject1` no campo nome do **projeto** .

4. No **Gerenciador de projetos**, clique com o botão direito do mouse em `Class1`e clique em **Propriedades**. A janela **Propriedades** da classe é exibida.

5. Altere a propriedade `Name` para `MathFunctions`.

6. No **Gerenciador de projetos**, clique com o botão direito do mouse em `MathFunctions`e clique em **Exibir código**. O **Editor de código** é exibido.

7. Adicione uma variável local para conter o valor da propriedade:

    ```vb
    ' Local variable to hold property value
    Private mvarProp1 As Integer
    ```

8. Adicione os procedimentos property `Let` e Property `Get` Property:

    ```vb
    Public Property Let Prop1(ByVal vData As Integer)
       'Used when assigning a value to the property.
       mvarProp1 = vData
    End Property
    Public Property Get Prop1() As Integer
       'Used when retrieving a property's value.
       Prop1 = mvarProp1
    End Property
    ```

9. Adicione uma função:

    ```vb
    Function AddNumbers(
       ByVal SomeNumber As Integer,
       ByVal AnotherNumber As Integer) As Integer

       AddNumbers = SomeNumber + AnotherNumber
    End Function
    ```

10. Crie e registre o objeto COM clicando em **Make ComObject1. dll** no menu **arquivo** .

    > [!NOTE]
    > Embora você também possa expor uma classe criada com Visual Basic como um objeto COM, ela não é um objeto COM verdadeiro e não pode ser usada neste passo-a-passos. Para obter detalhes, consulte [interoperabilidade com em aplicativos .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).

## <a name="interop-assemblies"></a>Assemblies de interoperabilidade

No procedimento a seguir, você criará um assembly de interoperabilidade, que atua como uma ponte entre código não gerenciado (como um objeto COM) e o código gerenciado que o Visual Studio usa. O assembly de interoperabilidade que o Visual Basic cria lida com muitos dos detalhes do trabalho com objetos COM, como o *marshaling de interoperabilidade*, o processo de empacotamento de parâmetros e valores de retorno em tipos de dados equivalentes à medida que eles se movem para e de objetos com. A referência no aplicativo Visual Basic aponta para o assembly de interoperabilidade, não o objeto COM real.

### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>Para usar um objeto com com Visual Basic 2005 e versões posteriores

1. Abra um novo projeto de aplicativo do Windows Visual Basic.

2. No menu **Projeto**, clique em **Adicionar Referência**.

     A caixa de diálogo **Adicionar Referência** é exibida.

3. Na guia **com** , clique duas vezes em `ComObject1` na lista **nome do componente** e clique em **OK**.

4. No menu **Projeto**, clique em **Adicionar Novo Item**.

     A caixa de diálogo **Adicionar Novo Item** é exibida.

5. No painel **modelos** , clique em **classe**.

     O nome de arquivo padrão, `Class1.vb`, aparece no campo **nome** . Altere esse campo para MathClass. vb e clique em **Adicionar**. Isso cria uma classe chamada `MathClass`e exibe seu código.

6. Adicione o seguinte código à parte superior de `MathClass` para herdar da classe COM.

     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]

7. Sobrecarregar o método público da classe base adicionando o seguinte código para `MathClass`:

     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]

8. Estenda a classe herdada adicionando o seguinte código para `MathClass`:

     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]

A nova classe herda as propriedades da classe base no objeto COM, sobrecarrega um método e define um novo método para estender a classe.

### <a name="to-test-the-inherited-class"></a>Para testar a classe herdada

1. Adicione um botão ao formulário de inicialização e clique duas vezes nele para exibir seu código.

2. No procedimento do manipulador de eventos `Click` do botão, adicione o seguinte código para criar uma instância do `MathClass` e chamar os métodos sobrecarregados:

     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]

3. Execute o projeto pressionando F5.

Quando você clica no botão no formulário, o método `AddNumbers` é chamado primeiro com `Short` números de tipo de dados e Visual Basic escolhe o método apropriado a partir da classe base. A segunda chamada para `AddNumbers` é direcionada para o método Overload de `MathClass`. A terceira chamada chama o método `SubtractNumbers`, que estende a classe. A propriedade na classe base é definida e o valor é exibido.

## <a name="next-steps"></a>{1&gt;Próximas etapas&lt;1}

Talvez você tenha notado que a função de `AddNumbers` sobrecarregada parece ter o mesmo tipo de dados do método herdado da classe base do objeto COM. Isso ocorre porque os argumentos e parâmetros do método de classe base são definidos como inteiros de 16 bits no Visual Basic 6,0, mas são expostos como inteiros de 16 bits do tipo `Short` em versões posteriores do Visual Basic. A nova função aceita inteiros de 32 bits e sobrecarrega a função de classe base.

Ao trabalhar com objetos COM, certifique-se de verificar o tamanho e os tipos de dados dos parâmetros. Por exemplo, ao usar um objeto COM que aceita um objeto de coleção Visual Basic 6,0 como um argumento, você não pode fornecer uma coleção de uma versão posterior do Visual Basic.

Propriedades e métodos herdados de classes COM podem ser substituídos, o que significa que você pode declarar uma propriedade ou um método local que substitui uma propriedade ou método herdado de uma classe COM base. As regras para substituir as propriedades COM herdadas são semelhantes às regras para substituir outras propriedades e métodos pelas seguintes exceções:

- Se você substituir qualquer propriedade ou método herdado de uma classe COM, deverá substituir todas as outras propriedades e métodos herdados.

- As propriedades que usam parâmetros de `ByRef` não podem ser substituídas.

## <a name="see-also"></a>Consulte também

- [Interoperabilidade COM em Aplicativos .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Tipo de Dados Short](../../../visual-basic/language-reference/data-types/short-data-type.md)
