---
title: Métodos de extensão (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: c34108b9eb53da77a48afb5d270dce9a32289c99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731108"
---
# <a name="extension-methods-visual-basic"></a>Métodos de extensão (Visual Basic)
Métodos de extensão permitem que os desenvolvedores adicionem funcionalidades personalizadas aos tipos de dados que já estão definidos sem criar um novo tipo derivado. Métodos de extensão tornam possível escrever um método que pode ser chamado como se fosse um método de instância do tipo existente.  
  
## <a name="remarks"></a>Comentários  
 Um método de extensão pode ser apenas um `Sub` procedimento ou uma `Function` procedimento. Você não pode definir uma propriedade de extensão, o campo ou o evento. Todos os métodos de extensão devem ser marcados com o atributo de extensão `<Extension()>` do <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.  
  
 O primeiro parâmetro em uma definição de método de extensão especifica qual tipo de dados, o método estende. Quando o método é executado, o primeiro parâmetro é associado à instância do tipo de dados que invoca o método.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir define uma `Print` extensão para o <xref:System.String> tipo de dados. Usa o método `Console.WriteLine` para exibir uma cadeia de caracteres. O parâmetro do `Print` método, `aString`, estabelece o método estende a <xref:System.String> classe.  
  
 [!code-vb[VbVbalrExtensionMethods#1](./codesnippet/VisualBasic/extension-methods_1.vb)]  
  
 Observe que a definição do método de extensão é marcada com o atributo de extensão `<Extension()>`. Marcar o módulo no qual o método é definido é opcional, mas cada método de extensão deve ser marcado. <xref:System.Runtime.CompilerServices> deve ser importado para acessar o atributo de extensão.  
  
 Métodos de extensão podem ser declarados apenas dentro de módulos. Normalmente, o módulo no qual um método de extensão é definido não é o mesmo módulo como aquele no qual ele é chamado. Em vez disso, o módulo que contém o método de extensão é importado, se ele precisar ser, para colocá-lo no escopo. Depois que o módulo que contém `Print` está no escopo, o método pode ser chamado como se fosse um método comum de instância que não usa argumentos, como `ToUpper`:  
  
 [!code-vb[VbVbalrExtensionMethods#2](./codesnippet/VisualBasic/extension-methods_2.vb)]  
  
 O exemplo a seguir, `PrintAndPunctuate`, também é uma extensão para <xref:System.String>, dessa vez definida com dois parâmetros. O primeiro parâmetro, `aString`, estabelece que o método de extensão estende <xref:System.String>. O segundo parâmetro, `punc`, deve ser uma cadeia de caracteres de pontuação que é passada como um argumento quando o método é chamado. O método exibe a cadeia de caracteres seguida por sinais de pontuação.  
  
 [!code-vb[VbVbalrExtensionMethods#3](./codesnippet/VisualBasic/extension-methods_3.vb)]  
  
 O método é chamado por meio do envio em um argumento de cadeia de caracteres para `punc`: `example.PrintAndPunctuate(".")`  
  
 A exemplo a seguir mostra `Print` e `PrintAndPunctuate` definidos e chamados. <xref:System.Runtime.CompilerServices> é importado no módulo de definição para habilitar o acesso ao atributo de extensão.  
  
### <a name="code"></a>Código  
  
```vb  
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
  
 Em seguida, os métodos de extensão são trazidos para o escopo e chamados.  
  
```vb  
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
  
### <a name="comments"></a>Comentários  
 Tudo que é necessário para poder executá-los ou métodos de extensão semelhante é que está no escopo. Se o módulo que contém um método de extensão está no escopo, ele está visível no IntelliSense e pode ser chamado como se fosse um método comum de instância.  
  
 Observe que quando os métodos são chamados, nenhum argumento é enviado para o primeiro parâmetro. Parâmetro `aString` o método anterior definições é associado a `example`, a instância do `String` que a chama. O compilador usará `example` como o argumento enviado para o primeiro parâmetro.  
  
 Se um método de extensão é chamado de um objeto que é definido como `Nothing`, o método de extensão é executado. Isso não se aplica aos métodos comum de instância. Você pode verificar explicitamente `Nothing` no método de extensão.  
  
## <a name="types-that-can-be-extended"></a>Tipos que podem ser estendidos  
 Você pode definir um método de extensão na maioria dos tipos que podem ser representados em uma lista de parâmetros do Visual Basic, incluindo o seguinte:  
  
-   Classes (tipos de referência)  
  
-   Estruturas (tipos de valor)  
  
-   Interfaces  
  
-   Delegados  
  
-   Argumentos ByRef e ByVal  
  
-   Parâmetros de método genérico  
  
-   Matrizes  
  
 Como o primeiro parâmetro especifica o tipo de dados que o método de extensão estende, ele é obrigatório e não pode ser opcional. Por esse motivo, `Optional` parâmetros e `ParamArray` parâmetros não podem ser o primeiro parâmetro na lista de parâmetros.  
  
 Métodos de extensão não são considerados na associação tardia. No exemplo a seguir, a instrução `anObject.PrintMe()` gera uma <xref:System.MissingMemberException> exceção, a mesma exceção que você veria se o segundo `PrintMe` definição de método de extensão foram excluídos.  
  
 [!code-vb[VbVbalrExtensionMethods#9](./codesnippet/VisualBasic/extension-methods_4.vb)]  
  
## <a name="best-practices"></a>Práticas recomendadas  
 Métodos de extensão fornecem uma maneira avançada e conveniente de estender um tipo existente. No entanto, para usá-las com êxito, há alguns pontos a considerar. Essas considerações se aplicam principalmente a autores de bibliotecas de classes, mas eles podem afetar qualquer aplicativo que usa métodos de extensão.  
  
 Mais geralmente, os métodos de extensão que você adiciona a tipos que não possuem são mais vulneráveis que métodos de extensão adicionados aos tipos que você controla. Várias coisas que podem ocorrer em classes que você não possui e que podem interferir com seus métodos de extensão.  
  
-   Se qualquer membro de instância acessível que tem uma assinatura que é compatível com os argumentos na instrução de chamada, com nenhuma conversões redutoras necessárias de argumento para o parâmetro existir, será usado o método de instância em preferência a qualquer método de extensão. Portanto, se um método de instância apropriado for adicionado a uma classe em algum momento, um membro de extensão existente que dependem de você pode se tornar inacessível.  
  
-   O autor de um método de extensão não pode impedir que outros programadores escrever métodos de extensão conflitantes que possam ter precedência sobre a extensão original.  
  
-   Você pode aumentar a robustez colocando métodos de extensão em seu próprio namespace. Os consumidores da sua biblioteca podem incluir um namespace ou excluí-lo ou selecionar entre namespaces, separadamente do restante da biblioteca.  
  
-   Ele pode ser mais seguro estender as interfaces de é estender classes, especialmente se você não possui a interface ou classe. Uma alteração em uma interface afeta todas as classes que a implementa. Portanto, o autor pode ser menos provável adicionar ou alterar os métodos em uma interface. No entanto, se uma classe implementa duas interfaces que têm os métodos de extensão com a mesma assinatura, nenhum método de extensão é visível.  
  
-   Estenda o tipo mais específico, que você pode. Em uma hierarquia de tipos, se você selecionar um tipo do qual muitos outros tipos são derivados, existem inúmeras possibilidades para a introdução de métodos de instância ou outros métodos de extensão que podem interferir com as suas.  
  
## <a name="extension-methods-instance-methods-and-properties"></a>Métodos de extensão, métodos de instância e propriedades  
 Quando um método de instância dentro do escopo tem uma assinatura que é compatível com os argumentos de uma instrução de chamada, o método de instância é escolhido em preferência a qualquer método de extensão. O método de instância terá precedência mesmo se o método de extensão é uma correspondência melhor. No exemplo a seguir `ExampleClass` contém um método de instância nomeado `ExampleMethod` que tem um parâmetro de tipo `Integer`. Método de extensão `ExampleMethod` estende `ExampleClass`, e tem um parâmetro de tipo `Long`.  
  
 [!code-vb[VbVbalrExtensionMethods#4](./codesnippet/VisualBasic/extension-methods_5.vb)]  
  
 A primeira chamada para `ExampleMethod` no código a seguir chama o método de extensão, porque `arg1` é `Long` e é compatível apenas com o `Long` parâmetro no método de extensão. A segunda chamada para `ExampleMethod` tem um `Integer` argumento, `arg2`, e ele chama o método de instância.  
  
 [!code-vb[VbVbalrExtensionMethods#5](./codesnippet/VisualBasic/extension-methods_6.vb)]  
  
 Agora você deve inverter os tipos de dados dos parâmetros nos dois métodos:  
  
 [!code-vb[VbVbalrExtensionMethods#6](./codesnippet/VisualBasic/extension-methods_7.vb)]  
  
 Desta vez, o código em `Main` chama o método de instância as duas vezes. Isso ocorre porque os dois `arg1` e `arg2` tem uma conversão de ampliação para `Long`, e o método de instância tem precedência sobre o método de extensão em ambos os casos.  
  
 [!code-vb[VbVbalrExtensionMethods#7](./codesnippet/VisualBasic/extension-methods_8.vb)]  
  
 Portanto, um método de extensão não pode substituir um método de instância existente. No entanto, quando um método de extensão tem o mesmo nome que um método de instância, mas as assinaturas não entram em conflito, ambos os métodos podem ser acessados. Por exemplo, se classe `ExampleClass` contém um método chamado `ExampleMethod` que não leva argumentos, os métodos de extensão com o mesmo nome mas assinaturas diferentes são permitidas, conforme mostrado no código a seguir.  
  
 [!code-vb[VbVbalrExtensionMethods#8](./codesnippet/VisualBasic/extension-methods_9.vb)]  
  
 A saída desse código é da seguinte maneira:  
  
 `Extension method`  
  
 `Instance method`  
  
 A situação é mais simples com propriedades: se um método de extensão tem o mesmo nome que uma propriedade de classe que estende, o método de extensão não estiver visível e não pode ser acessado.  
  
## <a name="extension-method-precedence"></a>Precedência do método de extensão  
 Quando dois métodos de extensão que possuem assinaturas idênticas estiverem no escopo e acessíveis, aquele com precedência mais alta será invocado. Precedência de um método de extensão se baseia no mecanismo usado para trazer o método para o escopo. A lista a seguir mostra a hierarquia de precedência, em ordem decrescente.  
  
1.  Métodos de extensão definidos dentro do módulo atual.  
  
2.  Métodos de extensão definidos dentro de dados tipos no namespace atual ou qualquer um de seus pais, com namespaces filhos que têm precedência maior do que namespaces pai.  
  
3.  Métodos de extensão definidos dentro de qualquer tipo de importação no arquivo atual.  
  
4.  Métodos de extensão definidos dentro de qualquer importação de namespace no arquivo atual.  
  
5.  Métodos de extensão definidos dentro de qualquer importação de tipo de nível de projeto.  
  
6.  Métodos de extensão definidos dentro de qualquer importação de namespace de nível de projeto.  
  
 Se a precedência não resolver a ambiguidade, você pode usar o nome totalmente qualificado para especificar o método que você está chamando. Se o `Print` método no exemplo anterior é definido em um módulo denominado `StringExtensions`, é o nome totalmente qualificado `StringExtensions.Print(example)` em vez de `example.Print()`.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Métodos de Extensão](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [Instrução Module](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Parâmetros Opcionais](./optional-parameters.md)
- [Matrizes de Parâmetros](./parameter-arrays.md)
- [Visão geral de atributos](../../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
