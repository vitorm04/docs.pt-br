---
title: "M&#233;todos de extens&#227;o (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ExtensionMethods"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "estendendo tipos de dados"
  - "métodos de extensão [Visual Basic]"
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
caps.latest.revision: 41
caps.handback.revision: 41
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# M&#233;todos de extens&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Métodos de extensão permitem que desenvolvedores adicionem funcionalidades personalizadas aos tipos de dados que já estão definidos sem criar um novo tipo derivado.  Métodos de extensão tornam possível gravar um método que pode ser chamado como se fosse um método de instância do tipo existente.  
  
## Comentários  
 Um método de extensão pode ser apenas um procedimento `Sub` ou `Function`.  Não é possível definir uma propriedade, um campo, ou um evento de extensão.  Todos os métodos de extensão devem ser marcados com o atributo de extensão `<Extension()>` do namespace <xref:System.Runtime.CompilerServices?displayProperty=fullName>.  
  
 O primeiro parâmetro de uma definição de método de extensão especifica o tipo de dado a partir do qual o método estende.  Quando o método é executado, o primeiro parâmetro é associado à instância do tipo de dados que chama o método.  
  
## Exemplo  
  
### Descrição  
 O exemplo a seguir define uma extensão `Print` para o tipo de dado <xref:System.String>.  O método usa `Console.WriteLine` para exibir uma cadeia de caracteres.  O parâmetro do método `Print`, `aString`, que estabelece o método estende a classe <xref:System.String>.  
  
 [!code-vb[VbVbalrExtensionMethods#1](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/extension-methods_1.vb)]  
  
 Observe que a definição do método de extensão é marcada com o atributo de extensão `<Extension()>`.  Marcar o módulo no qual o método é definido é opcional, mas cada método de extensão deve ser marcado.  <xref:System.Runtime.CompilerServices> deve ser importado para acessar o atributo de extensão.  
  
 Os métodos de extensão podem ser declarados apenas dentro de módulos.  Normalmente, o módulo no qual um método de extensão é definido não é o mesmo que o módulo no qual ele é chamado.  Em vez disso, o módulo que contém o método de extensão é importado, se necessário, para trazê\-lo no escopo.  Depois que o módulo que contém `Print` está no escopo, o método pode ser chamado como se fosse um método comum de instância que não leva argumentos, como `ToUpper`:  
  
 [!code-vb[VbVbalrExtensionMethods#2](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/extension-methods_2.vb)]  
  
 O exemplo a seguir, `PrintAndPunctuate`, também é uma extensão para <xref:System.String>, dessa vez definida com dois parâmetros.  O primeiro parâmetro, `aString`, estabelece que o método de extensão estende <xref:System.String>.  O segundo parâmetro, `punc`, deve ser uma cadeia de caracteres de pontuação passados como um argumento quando o método é chamado.  O método exibe a cadeia de caracteres seguida pela pontuação.  
  
 [!code-vb[VbVbalrExtensionMethods#3](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/extension-methods_3.vb)]  
  
 O método é chamado por meio do envio de um argumento de cadeia de caracteres para `punc`: `example.PrintAndPunctuate(".")`  
  
 O exemplo a seguir mostra `Print` e `PrintAndPunctuate` definidos e chamados.  <xref:System.Runtime.CompilerServices> é importado no módulo de definição para permitir o acesso ao atributo de extensão.  
  
### Código  
  
```vb#  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
  
    <Extension()>   
    Public Sub Print(ByVal aString As String)  
        Console.WriteLine(aString)  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 Em seguida, os métodos de extensão são colocador no escopo e chamados.  
  
```vb#  
Imports ConsoleApplication2.StringExtensions  
Module Module1  
  
    Sub Main()  
  
        Dim example As String = "Example string"  
        example.Print()  
  
        example = "Hello"  
        example.PrintAndPunctuate(".")  
        example.PrintAndPunctuate("!!!!")  
  
    End Sub  
End Module  
```  
  
### Comentários  
 Tudo que é necessário para poder executar esses métodos de extensão ou métodos semelhantes é que está no escopo.  Se o módulo que contém um método de extensão está no escopo, é visível no IntelliSense e pode ser chamado como se fosse um método comum de instância.  
  
 Observe que quando os métodos são chamados, nenhum argumento é enviado para o primeiro parâmetro.  O parâmetro `aString` nas definições de método anteriores está associado a `example`, a instância de `String` que a chama.  O compilador usará `example` como o argumento enviado ao primeiro parâmetro.  
  
 Se um método de extensão é chamado para um objeto que está definido como `Nothing`, o método de extensão é executado.  Isso não se aplica aos métodos comuns de instância.  É possível verificar explicitamente `Nothing` no método de extensão.  
  
## Tipos que podem ser estendidos  
 É possível definir um método de extensão na maioria tipos que podem ser representados em uma lista de parâmetros do Visual Basic, incluindo o seguinte:  
  
-   Classes \(tipos de referência\)  
  
-   Estruturas \(tipos de valor\)  
  
-   Interfaces  
  
-   Delegados  
  
-   Argumentos ByRef e ByVal  
  
-   Parâmetros de método genérico  
  
-   Matrizes  
  
 Como o primeiro parâmetro especifica o tipo de dados que o método de extensão estende, ele é obrigatório e não pode ser opcional.  Por esse motivo, os parâmetros `Optional` e os parâmetros `ParamArray` não podem ser o primeiro parâmetro na lista de parâmetros.  
  
 Métodos de extensão não são considerados na associação tardia.  No exemplo a seguir, a instrução `anObject.PrintMe()` gera uma exceção de <xref:System.MissingMemberException>, a mesma exceção que você veria se a segunda definição de método de extensão `PrintMe` fosse excluída.  
  
 [!code-vb[VbVbalrExtensionMethods#9](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/extension-methods_4.vb)]  
  
## Práticas recomendadas  
 Métodos de extensão fornecem uma maneira conveniente e eficiente de estender um tipo existente.  No entanto, para usá\-las com êxito, há alguns pontos a serem considerados.  Essas considerações se aplicam principalmente a autores de bibliotecas de classe, mas podem afetar qualquer aplicativo que usar métodos de extensão.  
  
 Mais comumente, os métodos de extensão que você adiciona a tipos que não são de sua propriedade são mais vulneráveis que métodos de extensão adicionados aos tipos que você controla.  Um número de itens pode ocorrer em classes que você não possui e isso pode interferir em seus métodos de extensão.  
  
-   Se existe qualquer membro de instância acessível que tenha uma assinatura compatível com os argumentos na instrução de chamada, sem as conversões redutoras necessárias de argumento para o parâmetro, o método de instância será usado de preferência a qualquer método de extensão.  Portanto, se um método de instância apropriado for adicionado a uma classe em algum ponto, um membro de extensão existente em que você se baseia se tornará inacessível.  
  
-   O autor de um método de extensão não pode impedir que outros programadores escrevam métodos de extensão conflitantes que possam ter precedência sobre a extensão original.  
  
-   É possível melhorar a robustez colocando métodos de extensão em seu próprio namespace.  Os consumidores de sua biblioteca podem incluir um namespace ou exclui\-lo, ou selecionar entre namespaces, separadamente do restante da biblioteca.  
  
-   Pode ser mais seguro estender as interfaces de estender classes, especialmente se você não possui a interface ou classe.  Uma alteração em uma interface afeta todas as classe que a implementa.  Portanto, é menos provável que o autor adicione ou altere métodos em uma interface.  No entanto, se uma classe implementa duas interfaces que possuem métodos de extensão com a mesma assinatura, nenhum método de extensão é visível.  
  
-   Estender o tipo mais específico que você pode.  Em uma hierarquia de tipos, se você selecionar um tipo do qual muitos outros tipos são derivados, existem inúmeras possibilidades para a introdução dos métodos de instância ou outros métodos de extensão que podem interferir no seu.  
  
## Métodos de extensão, métodos de instância e propriedades  
 Quando um método de instância de em escopo possuir uma assinatura compatível com os argumentos de uma instrução de chamada, o método de instância é escolhido em preferência a qualquer método de extensão.  O método de instância terá precedência mesmo se o método de extensão for uma correspondência melhor.  No exemplo a seguir, `ExampleClass` contém um método de instância nomeado `ExampleMethod` que tem um parâmetro do tipo `Integer`.  O método de extensão `ExampleMethod` estende `ExampleClass` e tem um parâmetro do tipo `Long`.  
  
 [!code-vb[VbVbalrExtensionMethods#4](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/extension-methods_5.vb)]  
  
 A primeira chamada para `ExampleMethod` no código a seguir chama o método de extensão, porque `arg1` é `Long` e é compatível somente com o parâmetro `Long` no método de extensão.  A segunda chamada para `ExampleMethod` tem um argumento de `Integer` , `arg2` e chama o método de instância.  
  
 [!code-vb[VbVbalrExtensionMethods#5](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/extension-methods_6.vb)]  
  
 Agora você deve inverter os tipos de dados dos parâmetros nos dois métodos:  
  
 [!code-vb[VbVbalrExtensionMethods#6](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/extension-methods_7.vb)]  
  
 Desta vez, o código em `Main` chama o método de instância as duas vezes.  Isso ocorre porque `arg1` e `arg2` têm uma conversão de ampliação para `Long`, e o método de instância tem precedência sobre o método de extensão em ambos os casos.  
  
 [!code-vb[VbVbalrExtensionMethods#7](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/extension-methods_8.vb)]  
  
 Dessa forma, um método de extensão não pode substituir um método de instância existente.  No entanto, quando um método de extensão tem o mesmo nome que um método de instância, mas as assinaturas não entram em conflito, ambos os métodos podem ser acessados.  Por exemplo, se a classe `ExampleClass` contém um método chamado `ExampleMethod` que não leva argumentos, os métodos de extensão com o mesmo nome mas com assinaturas diferentes são permitidos, conforme mostrado no código a seguir.  
  
 [!code-vb[VbVbalrExtensionMethods#8](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/extension-methods_9.vb)]  
  
 A saída desse código é a seguinte:  
  
 `Extension method`  
  
 `Instance method`  
  
 A situação é mais simples com propriedades: se um método de extensão tiver o mesmo nome de uma propriedade da classe que estende, o método de extensão não estará visível e não poderá ser acessado.  
  
## Precedência do método de extensão  
 Quando dois métodos de extensão que possuem assinaturas idênticas estiverem no escopo e forem acessíveis, aquele com precedência mais alta será invocado.  A precedência de um método de extensão é baseada no mecanismo usado para transferir o método para o escopo.  A lista a seguir mostra a hierarquia de precedência, da mais alta para a mais baixa.  
  
1.  Métodos de extensão definidos dentro do módulo atual.  
  
2.  Métodos de extensão definidos dentro de tipos de dados no namespace atual ou em qualquer um de seus pais, com namespaces filhos que têm precedência maior do que namespaces pai.  
  
3.  Métodos de extensão definidos dentro de qualquer importação de tipo no arquivo atual.  
  
4.  Métodos de extensão definidos dentro de qualquer importação de namespace no arquivo atual.  
  
5.  Métodos de extensão definidos dentro de qualquer importação no nível do projeto.  
  
6.  Métodos de extensão definidos dentro de qualquer importação de namespace no nível do projeto.  
  
 Se a precedência não resolver a ambiguidade, você pode usar o nome totalmente qualificado para especificar o método que você está chamando.  Se o método `Print` no exemplo anterior é definido em um módulo chamado `StringExtensions`, o nome totalmente qualificado é `StringExtensions.Print(example)` em vez de `example.Print()`.  
  
## Consulte também  
 <xref:System.Runtime.CompilerServices>   
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [Métodos de extensão](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)   
 [Instrução Module](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Parâmetros opcionais](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Matrizes de parâmetros](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)