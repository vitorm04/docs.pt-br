---
title: 'Passo a passo: Implementando a herança com objetos COM (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: 0b3977e73e3b2aa9e80e2dab08d15035283b8387
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022318"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>Passo a passo: Implementando a herança com objetos COM (Visual Basic)
Você pode derivar classes de Visual Basic de `Public` classes em objetos COM, mesmo aqueles criados em versões anteriores do Visual Basic. As propriedades e métodos das classes herdadas de objetos COM a podem ser substituídos ou sobrecarregados assim como as propriedades e métodos de qualquer outra classe base podem ser substituídos ou sobrecarregados. Herança de objetos COM é útil quando você tiver uma biblioteca de classe existente que você não deseja recompilar.  
  
 O procedimento a seguir mostra como usar o Visual Basic 6.0 para criar um objeto COM que contém uma classe e, em seguida, usá-lo como uma classe base.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>Para criar o objeto COM que é usado neste passo a passo  
  
1. No Visual Basic 6.0, abra um novo projeto de DLL do ActiveX. Um projeto chamado `Project1` é criado. Ele tem uma classe chamada `Class1`.  
  
2. No **Explorador de projeto**, clique com botão direito **Projeto1**e, em seguida, clique em **Projeto1 propriedades**. O **propriedades do projeto** caixa de diálogo é exibida.  
  
3. No **gerais** guia da **propriedades do projeto** caixa de diálogo, altere o nome do projeto, digitando `ComObject1` no **nome do projeto** campo.  
  
4. No **Explorador de projeto**, clique com botão direito `Class1`e, em seguida, clique em **propriedades**. O **propriedades** janela para a classe é exibida.  
  
5. Alterar o `Name` propriedade para `MathFunctions`.  
  
6. No **Explorador de projeto**, clique com botão direito `MathFunctions`e, em seguida, clique em **Exibir código**. O **Editor de códigos** é exibida.  
  
7. Adicione uma variável local para armazenar o valor da propriedade:  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8. Adicionar propriedade `Let` e a propriedade `Get` procedimentos de propriedade:  
  
    ```  
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
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. Criar e registrar o objeto COM, clicando em **tornar ComObject1.dll** sobre o **arquivo** menu.  
  
    > [!NOTE]
    >  Embora você também pode expor uma classe criada com o Visual Basic como um objeto COM, ele não é um objeto COM real e não pode ser usado neste passo a passo. Para obter detalhes, consulte [interoperabilidade COM em aplicativos do .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="interop-assemblies"></a>Assemblies de interoperabilidade  
 O procedimento a seguir, você criará um assembly de interoperabilidade, que atua como uma ponte entre o código não gerenciado (por exemplo, um objeto COM) e o código gerenciado que usa o Visual Studio. O assembly de interoperabilidade do Visual Basic cria lida com muitos dos detalhes de como trabalhar com objetos COM, como *marshaling de interoperabilidade*, o processo de compactação parâmetros e valores de retorno em dados equivalentes tipos quando eles passam a e de objetos COM. A referência no aplicativo Visual Basic aponta para o assembly de interoperabilidade, não o objeto COM real.  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>Usar um objeto COM o Visual Basic 2005 e versões posteriores  
  
1. Abra um novo projeto de aplicativo do Windows Visual Basic.  
  
2. No menu **Projeto**, clique em **Adicionar Referência**.  
  
     A caixa de diálogo **Adicionar Referência** é exibida.  
  
3. Sobre o **COM** guia, clique duas vezes `ComObject1` no **nome do componente** lista e clique em **Okey**.  
  
4. No menu **Projeto**, clique em **Adicionar Novo Item**.  
  
     A caixa de diálogo **Adicionar Novo Item** é exibida.  
  
5. No **modelos** painel, clique em **classe**.  
  
     O nome de arquivo padrão, `Class1.vb`, é exibida na **nome** campo. Altere este campo para MathClass.vb e clique em **adicionar**. Isso cria uma classe chamada `MathClass`e exibe seu código.  
  
6. Adicione o seguinte código na parte superior do `MathClass` herdar da classe COM.  
  
     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]  
  
7. Sobrecarregar o método público da classe base, adicionando o seguinte código ao `MathClass`:  
  
     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]  
  
8. Estender a classe herdada adicionando o seguinte código ao `MathClass`:  
  
     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]  
  
 A nova classe herda as propriedades da classe base no objeto COM, sobrecarrega um método e define um novo método para estender a classe.  
  
#### <a name="to-test-the-inherited-class"></a>Para testar a classe herdada  
  
1. Adicione um botão ao seu formulário de inicialização e, em seguida, clique duas vezes nele para exibir seu código.  
  
2. O botão `Click` procedimento do manipulador de eventos, adicione o seguinte código para criar uma instância de `MathClass` e chamar os métodos sobrecarregados:  
  
     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]  
  
3. Execute o projeto pressionando F5.  
  
 Quando você clica no botão no formulário, o `AddNumbers` método é chamado pela primeira vez com `Short` números, tipo de dados e o Visual Basic escolhe o método apropriado da classe base. A segunda chamada para `AddNumbers` é direcionado para o método de sobrecarga de `MathClass`. A terceira chamada chama o `SubtractNumbers` método, que estende a classe. A propriedade na classe base é definida, e o valor é exibido.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você deve ter observado que sobrecarregado `AddNumbers` função parece ter os mesmos dados de tipo que o método herdado da classe base do objeto COM. Isso ocorre porque os argumentos e os parâmetros de método da classe base são definidos como inteiros de 16 bits no Visual Basic 6.0, mas eles são expostos como inteiros de 16 bits do tipo `Short` em versões posteriores do Visual Basic. A nova função aceita inteiros de 32 bits e sobrecargas de função da classe base.  
  
 Ao trabalhar com objetos COM, certifique-se de que você verifique os tipos de dados e tamanho dos parâmetros. Por exemplo, quando você estiver usando um objeto COM que aceita um objeto de coleção do Visual Basic 6.0 como um argumento, você não pode fornecer uma coleção de uma versão posterior do Visual Basic.  
  
 As propriedades e métodos herdados de classes COM podem ser substituídos, que significa que você pode declarar uma propriedade local ou um método que substitui uma propriedade ou método herdado de uma classe base do COM. As regras para a substituição COM as propriedades herdadas são semelhantes às regras para a substituição de outras propriedades e métodos com as seguintes exceções:  
  
- Se você substituir qualquer propriedade ou método herdado de uma classe COM, você deve substituir todas as outras propriedades herdadas e métodos.  
  
- As propriedades que usam `ByRef` parâmetros não podem ser substituídos.  
  
## <a name="see-also"></a>Consulte também

- [Interoperabilidade COM em Aplicativos .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Tipo de Dados Short](../../../visual-basic/language-reference/data-types/short-data-type.md)
