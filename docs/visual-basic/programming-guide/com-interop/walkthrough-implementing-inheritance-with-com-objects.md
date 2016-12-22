---
title: "Instru&#231;&#245;es passo a passo: implementando a heran&#231;a com objetos COM (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "classes base, capacidade de reutilização COM"
  - "classes derivadas, capacidade de reutilização COM"
  - "herança, capacidade de reutilização COM"
  - "herança, explicações passo a passo"
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: implementando a heran&#231;a com objetos COM (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode derivar classes de Visual Basic de `Public` classes de objetos COM, mesmo aqueles criados em versões anteriores do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  As propriedades e métodos das classes herdadas de objetos COM podem ser substituídos ou sobrecarregados assim como propriedades e métodos de qualquer outra classe base podem ser substituídos ou sobrecarregados.  Herança de objetos COM é útil quando você tem uma biblioteca de classe existente que você não deseja recompilar.  
  
 O procedimento a seguir mostra como usar o Visual Basic 6.0 para criar um objeto COM que contém uma classe e usá\-lo como uma classe base.  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Para criar o objeto COM usado nesta explicação passo a passo  
  
1.  No Visual Basic 6.0, abra um novo projeto de DLL de ActiveX.  Um projeto chamado `Project1` é criado.  Ele tem uma classe chamada `Class1`.  
  
2.  No  **Project Explorer**, com o botão direito  **Projeto1**e, em seguida, clique em  **Propriedades de Projeto1**.  O  **Propriedades do projeto** caixa de diálogo é exibida.  
  
3.  No  **Geral** guia da  **Propriedades do projeto** diálogo, altere o nome do projeto digitando `ComObject1` na  **Nome do projeto** campo.  
  
4.  No  **Project Explorer**, com o botão direito `Class1`e, em seguida, clique em  **Propriedades**.  O  **Propriedades** janela para a classe é exibida.  
  
5.  Alterar o `Name` propriedade para `MathFunctions`.  
  
6.  No  **Project Explorer**, com o botão direito `MathFunctions`e, em seguida, clique em  **Exibir código**.  O  **O Editor de código** é exibida.  
  
7.  Adicione uma variável local para armazenar o valor da propriedade:  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  Adicionar propriedade de `Let` e a propriedade `Get` os procedimentos de propriedade:  
  
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
  
10. Criar e registrar o objeto COM, clicando em  **ComObject1.dll fazer** sobre o  **arquivo** menu.  
  
    > [!NOTE]
    >  Embora você também pode expor uma classe criada com [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] como um objeto COM, ele não é um objeto do COM verdadeiro e não podem ser usado nesta explicação.  Para obter detalhes, consulte:[Interoperabilidade COM em aplicativos .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## Assemblies de interoperabilidade  
 O procedimento a seguir, você criará um assembly de interoperabilidade, que atua como uma ponte entre o código não gerenciado \(como um objeto COM\) e o código gerenciado [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] usa.  O assembly de interoperabilidade que [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cria alças muitos detalhes de como trabalhar com objetos, tais como  *interop marshaling*, o processo de parâmetros de empacotamento e valores de retorno em dados equivalentes tipos à medida que mudam para e de objetos COM.  A referência a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pontos do aplicativo para o assembly de interoperabilidade, não o objeto COM real.  
  
#### Para usar um objeto COM o Visual Basic 2005 e versões posteriores  
  
1.  Abra um novo projeto de Aplicativo do Windows [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
2.  No menu **Project**, escolha **Add Reference**.  
  
     A caixa de diálogo **Add Reference** é exibida.  
  
3.  No  **COM** da sala, clique duas vezes em `ComObject1` na  **Nome do componente** lista e clique em  **OK**.  
  
4.  No menu **Project**, clique em **Add New Item**.  
  
     A caixa de diálogo **Add New Item** é exibida.  
  
5.  No  **modelos de** painel, clique em  **classe**.  
  
     O nome de arquivo padrão, `Class1.vb`, consta o  **nome** campo.  Alterar este campo para MathClass.vb e clique em  **Add**.  Isso cria uma classe chamada `MathClass`e exibe seu código.  
  
6.  Adicione o seguinte código para o topo da `MathClass` para herdar da classe COM.  
  
     [!CODE [VbVbalrInterop#31](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#31)]  
  
7.  Sobrecarregar o método público da classe base, adicionando o seguinte código para `MathClass`:  
  
     [!CODE [VbVbalrInterop#32](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#32)]  
  
8.  Estende a classe herdada, adicionando o seguinte código para `MathClass`:  
  
     [!CODE [VbVbalrInterop#33](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#33)]  
  
 A nova classe herda as propriedades da classe base no objeto COM, sobrecarrega um método e define um novo método para estender a classe.  
  
#### Para testar a classe herdada  
  
1.  Adicionar um botão no formulário de inicialização e, em seguida, clique duas vezes nele para exibir seu código.  
  
2.  O botão `Click` procedimento manipulador de evento, adicione o seguinte código para criar uma instância de `MathClass` e chamar os métodos sobrecarregados:  
  
     [!CODE [VbVbalrInterop#34](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#34)]  
  
3.  Execute o projeto pressionando F5.  
  
 Quando você clica no botão no formulário, o `AddNumbers` método é chamado pela primeira vez com `Short` tipo de dados de números, e [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] escolhe o método apropriado da classe base.  A segunda chamada para `AddNumbers` é direcionada para o método de sobrecarga do `MathClass`.  A terceira chamada chamadas a `SubtractNumbers` método, que estende a classe.  A propriedade na classe base é definida e o valor é exibido.  
  
## Próximas etapas  
 Você deve ter notado que o sobrecarregado `AddNumbers` função parece ter os dados do mesmos tipo que o método herdado da classe base do objeto COM.  Isso ocorre porque os argumentos e os parâmetros do método de classe base são definidos como números inteiros de 16 bits em Visual Basic 6.0, mas eles são expostos como inteiros de 16 bits do tipo `Short` em versões posteriores do Visual Basic.  A nova função aceita inteiros de 32 bits e sobrecarrega a função da classe base.  
  
 Ao trabalhar com objetos COM, certifique\-se de que você verifique se o tamanho e tipos de dados de parâmetros.  Por exemplo, quando você estiver usando um objeto COM que aceita um objeto da coleção Visual Basic 6.0 como um argumento, você não pode fornecer uma coleção de uma versão posterior do Visual Basic.  
  
 Propriedades e métodos herdados de classes COM podem ser substituídos, o que significa que você pode declarar uma propriedade local ou o método que substitui uma propriedade ou método herdado de uma classe base do COM.  As regras para a substituição COM as propriedades herdadas são semelhantes às regras de substituição de outras propriedades e métodos com as seguintes exceções:  
  
-   Se você substituir qualquer propriedade ou método herdado de uma classe COM, você deve substituir todas as outras propriedades herdadas e métodos.  
  
-   Propriedades que usam `ByRef` parâmetros não podem ser substituídos.  
  
## Consulte também  
 [Interoperabilidade COM em aplicativos .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)   
 [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Tipo de dados curto](../../../visual-basic/language-reference/data-types/short-data-type.md)