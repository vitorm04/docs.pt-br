---
title: "Métodos de extensão (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ExtensionMethods
dev_langs:
- VB
helpviewer_keywords:
- extending data types
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
caps.latest.revision: 41
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 381fa0db2d92590d23ebd71a7823a8465e94a6e6
ms.lasthandoff: 03/13/2017

---
# <a name="extension-methods-visual-basic"></a>Métodos de extensão (Visual Basic)
Métodos de extensão permitem aos desenvolvedores adicionar funcionalidade personalizada para tipos de dados que já foram definidos sem criar um novo tipo derivado. Métodos de extensão permitem escrever um método que pode ser chamado como se fosse um método de instância do tipo existente.  
  
## <a name="remarks"></a>Comentários  
 Um método de extensão pode ser apenas um `Sub` procedimento ou uma `Function` procedimento. Você não pode definir uma propriedade de extensão, o campo ou o evento. Todos os métodos de extensão devem ser marcados com o atributo de extensão `<Extension()>` do <xref:System.Runtime.CompilerServices?displayProperty=fullName>namespace.</xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 O primeiro parâmetro em uma definição de método de extensão especifica o tipo de dados o método estende. Quando o método for executado, o primeiro parâmetro é associado à instância do tipo de dados que chama o método.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir define uma `Print` extensão para o <xref:System.String>tipo de dados.</xref:System.String> Usa o método `Console.WriteLine` para exibir uma cadeia de caracteres. O parâmetro do `Print` método `aString`, estabelece o método estende a <xref:System.String>classe.</xref:System.String>  
  
 [!code-vb[VbVbalrExtensionMethods n º&1;](./codesnippet/VisualBasic/extension-methods_1.vb)]  
  
 Observe que a definição do método de extensão é marcada com o atributo de extensão `<Extension()>`. O módulo no qual o método é definido de marcação é opcional, mas cada método de extensão deve ser marcado. <xref:System.Runtime.CompilerServices>deve ser importado para acessar o atributo de extensão.</xref:System.Runtime.CompilerServices>  
  
 Métodos de extensão podem ser declarados dentro de módulos. Normalmente, o módulo no qual é definido um método de extensão não é o mesmo módulo aquele no qual ele é chamado. Em vez disso, o módulo que contém o método de extensão é importado, se ele precisa fazer para colocá-lo no escopo. Após o módulo que contém `Print` está no escopo, o método pode ser chamado como se fosse um método de instância comum que leva sem argumentos, como `ToUpper`:  
  
 [!code-vb[VbVbalrExtensionMethods n º&2;](./codesnippet/VisualBasic/extension-methods_2.vb)]  
  
 O exemplo a seguir, `PrintAndPunctuate`, também é uma extensão para <xref:System.String>, desta vez, definido com dois parâmetros.</xref:System.String> O primeiro parâmetro, `aString`, estabelece o método de extensão estende <xref:System.String>.</xref:System.String> O segundo parâmetro, `punc`, deve ser uma cadeia de caracteres de pontuação que é passada como um argumento quando o método é chamado. O método exibe a cadeia de caracteres seguida as marcas de pontuação.  
  
 [!code-vb[VbVbalrExtensionMethods n º&3;](./codesnippet/VisualBasic/extension-methods_3.vb)]  
  
 O método é chamado através do envio de um argumento de cadeia de caracteres para `punc`:`example.PrintAndPunctuate(".")`  
  
 A exemplo a seguir mostra `Print` e `PrintAndPunctuate` definidos e chamada. <xref:System.Runtime.CompilerServices>é importado no módulo de definição para habilitar o acesso ao atributo de extensão.</xref:System.Runtime.CompilerServices>  
  
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
 Tudo o que é necessário para poder executá-los ou métodos de extensão semelhantes é que eles sejam no escopo. Se o módulo que contém um método de extensão estiver no escopo, ele fica visível no IntelliSense e pode ser chamado como se fosse um método de instância comum.  
  
 Observe que quando os métodos são chamados, nenhum argumento é enviado para o primeiro parâmetro. Parâmetro `aString` no método anterior definições está associado a `example`, a instância de `String` que os chama. O compilador usará `example` como o argumento enviado para o primeiro parâmetro.  
  
 Se um método de extensão é chamado de um objeto é definido como `Nothing`, o método de extensão é executado. Isso não se aplica aos métodos de instância comum. Você pode verificar explicitamente `Nothing` no método de extensão.  
  
## <a name="types-that-can-be-extended"></a>Tipos que podem ser estendidos  
 Você pode definir um método de extensão na maioria dos tipos que podem ser representados em uma lista de parâmetros do Visual Basic, incluindo o seguinte:  
  
-   Classes (tipos de referência)  
  
-   Estruturas (tipos de valor)  
  
-   Interfaces  
  
-   Delegados  
  
-   Argumentos ByRef e ByVal  
  
-   Parâmetros de método genérico  
  
-   Matrizes  
  
 Como o primeiro parâmetro especifica o tipo de dados que estende o método de extensão, é necessário e não pode ser opcional. Por esse motivo, `Optional` parâmetros e `ParamArray` parâmetros não podem ser o primeiro parâmetro na lista de parâmetros.  
  
 Métodos de extensão não são considerados na ligação tardia. No exemplo a seguir, a instrução `anObject.PrintMe()` gera um <xref:System.MissingMemberException>exceção, a mesma exceção que você veria se o segundo `PrintMe` definição do método de extensão foram excluídos.</xref:System.MissingMemberException>  
  
 [!code-vb[VbVbalrExtensionMethods n º&9;](./codesnippet/VisualBasic/extension-methods_4.vb)]  
  
## <a name="best-practices"></a>Práticas recomendadas  
 Métodos de extensão fornecem uma maneira poderosa e conveniente de estender um tipo existente. No entanto, para usá-las com êxito, há alguns pontos a considerar. Essas considerações se aplicam principalmente para autores de bibliotecas de classes, mas eles podem afetar qualquer aplicativo que usa os métodos de extensão.  
  
 Mais geralmente, os métodos de extensão que você adicionar a tipos que não possuem são mais vulneráveis que adicionados aos tipos que você controle os métodos de extensão. Várias coisas podem ocorrer em classes que você não possui e que podem interferir com seus métodos de extensão.  
  
-   Se houver qualquer membro de instância acessível tem uma assinatura que é compatível com os argumentos na instrução de chamada, com nenhuma restrição conversões necessárias do argumento para o parâmetro, o método de instância será usado em vez de qualquer método de extensão. Portanto, se um método de instância apropriado é adicionado a uma classe em algum momento, um membro existente de extensão que você depende pode se tornar inacessível.  
  
-   O autor de um método de extensão não pode impedir que outros programadores escrevendo conflitantes métodos de extensão que podem ter precedência sobre a extensão original.  
  
-   Você pode aumentar a robustez colocando os métodos de extensão em seu próprio namespace. Os consumidores de sua biblioteca podem incluir um namespace ou excluí-la ou selecionar entre namespaces, separadamente do restante da biblioteca.  
  
-   Ele pode ser mais seguro estender interfaces que estender as classes, especialmente se você não possui a interface ou classe. Uma alteração em uma interface afeta todas as classes que a implementa. Portanto, o autor pode ser menos provável adicionar ou alterar os métodos em uma interface. No entanto, se uma classe implementa duas interfaces com métodos de extensão com a mesma assinatura, nenhum método de extensão é visível.  
  
-   Estenda o tipo mais específico, que você pode. Em uma hierarquia de tipos, se você selecionar um tipo do qual muitos outros tipos são derivados, há camadas de possibilidades para a introdução de métodos de instância ou outros métodos de extensão que podem interferir com as suas.  
  
## <a name="extension-methods-instance-methods-and-properties"></a>Métodos de extensão, os métodos de instância e propriedades  
 Quando um método de instância no escopo tem uma assinatura compatível com os argumentos de uma instrução de chamada, o método de instância é escolhido em vez de qualquer método de extensão. O método de instância tem precedência, mesmo se o método de extensão é uma correspondência melhor. No exemplo a seguir, `ExampleClass` contém um método de instância chamado `ExampleMethod` que tem um parâmetro do tipo `Integer`. Método de extensão `ExampleMethod` estende `ExampleClass`, e tem um parâmetro do tipo `Long`.  
  
 [!code-vb[VbVbalrExtensionMethods n º&4;](./codesnippet/VisualBasic/extension-methods_5.vb)]  
  
 A primeira chamada para `ExampleMethod` no código a seguir chama o método de extensão, como `arg1` é `Long` e é compatível apenas com o `Long` parâmetro no método de extensão. A segunda chamada para `ExampleMethod` tem um `Integer` argumento, `arg2`, e chama o método de instância.  
  
 [!code-vb[VbVbalrExtensionMethods n º&5;](./codesnippet/VisualBasic/extension-methods_6.vb)]  
  
 Agora reverte os tipos de dados dos parâmetros nos dois métodos:  
  
 [!code-vb[VbVbalrExtensionMethods n º&6;](./codesnippet/VisualBasic/extension-methods_7.vb)]  
  
 Dessa vez o código em `Main` chama o método de instância nas duas vezes. Isso ocorre porque ambos `arg1` e `arg2` tem uma conversão de ampliação para `Long`, e o método de instância tem precedência sobre o método de extensão em ambos os casos.  
  
 [!code-vb[VbVbalrExtensionMethods&#7;](./codesnippet/VisualBasic/extension-methods_8.vb)]  
  
 Portanto, um método de extensão não pode substituir um método de instância existente. No entanto, quando um método de extensão tem o mesmo nome que um método de instância, mas as assinaturas não entrem em conflito, os dois métodos podem ser acessados. Por exemplo, se classe `ExampleClass` contém um método chamado `ExampleMethod` que leva sem argumentos, os métodos de extensão com o mesmo nome mas assinaturas diferentes são permitidas, conforme mostrado no código a seguir.  
  
 [!code-vb[VbVbalrExtensionMethods n º&8;](./codesnippet/VisualBasic/extension-methods_9.vb)]  
  
 A saída desse código é da seguinte maneira:  
  
 `Extension method`  
  
 `Instance method`  
  
 A situação é mais simples com propriedades: se um método de extensão tem o mesmo nome que uma propriedade da classe que estende a ele, o método de extensão não estiver visível e não pode ser acessado.  
  
## <a name="extension-method-precedence"></a>Precedência do método de extensão  
 Quando dois métodos de extensão possuem assinaturas idênticas estão no escopo e acessível, aquela com a precedência mais alta será invocada. Precedência de um método de extensão se baseia o mecanismo usado para trazer o método para o escopo. A lista a seguir mostra a hierarquia de precedência, em ordem decrescente.  
  
1.  Métodos de extensão definidos dentro do módulo atual.  
  
2.  Métodos de extensão definidos nos dados tipos no namespace atual ou qualquer um de seus pais, com os namespaces filho ter precedência maior do que espaços para nome do pai.  
  
3.  Métodos de extensão definidos em imports qualquer tipo no arquivo atual.  
  
4.  Métodos de extensão definidos nas importações de namespace no arquivo atual.  
  
5.  Métodos de extensão definidos em qualquer tipo de nível de projeto imports.  
  
6.  Métodos de extensão definidos nas importações de namespace de nível de projeto.  
  
 Se a precedência não resolver a ambiguidade, você pode usar o nome totalmente qualificado para especificar o método que você está chamando. Se o `Print` método no exemplo anterior é definido em um módulo denominado `StringExtensions`, o nome totalmente qualificado é `StringExtensions.Print(example)` em vez de `example.Print()`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices></xref:System.Runtime.CompilerServices>   
 <xref:System.Runtime.CompilerServices.ExtensionAttribute></xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [Métodos de extensão](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)   
 [Instrução Module](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Parâmetros opcionais](./optional-parameters.md)   
 [Matrizes de parâmetros](./parameter-arrays.md)   
 [Visão geral de atributos](../../../../visual-basic/programming-guide/concepts/attributes/index.md)   
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
