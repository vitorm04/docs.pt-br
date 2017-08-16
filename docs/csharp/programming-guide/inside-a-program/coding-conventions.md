---
title: "Convenções de codificação em C# (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
caps.latest.revision: 32
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9f32fdc0eb1954cdac30c39e05c74d43301d850c
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="c-coding-conventions-c-programming-guide"></a>Convenções de codificação em C# (Guia de Programação em C#)
A [Especificação da Linguagem C#](http://go.microsoft.com/fwlink/?LinkId=199552) não define um padrão de codificação. No entanto, as diretrizes neste tópico são usadas pela Microsoft para desenvolver amostras e documentação.  
  
 As convenções de codificação atendem às seguintes finalidades:  
  
-   Criam uma aparência consistente para o código, para que os leitores possam se concentrar no conteúdo e não no layout.  
  
-   Permitem que os leitores entendam o código com mais rapidez, fazendo suposições com base na experiência anterior.  
  
-   Facilitam a cópia, a alteração e a manutenção do código.  
  
-   Demonstram as práticas recomendadas do C#.  
  
## <a name="naming-conventions"></a>Convenções de nomenclatura  
  
-   Em exemplos curtos que não incluem [diretivas using](../../../csharp/language-reference/keywords/using-directive.md), use as qualificações do namespace. Se você souber que um namespace é importado por padrão em um projeto, não precisará qualificar totalmente os nomes desse namespace. Nomes qualificados podem ser interrompidos após um ponto (.) se forem muito longos para uma única linha, conforme mostrado no exemplo a seguir.  
  
     [!code-cs[csProgGuideCodingConventions#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_1.cs)]  
  
-   Não é necessário alterar os nomes de objetos que foram criados usando as ferramentas de designer do Visual Studio para adequá-los a outras diretrizes.  
  
## <a name="layout-conventions"></a>Convenções de Layout  
 Um bom layout usa formatação para enfatizar a estrutura do código e para facilitar a leitura de código. Exemplos e amostras Microsoft estão em conformidade com as seguintes convenções:  
  
-   Use as configurações padrão do Editor de códigos (recuo inteligente, recuos de quatro caracteres, guias salvas como espaços). Para obter mais informações, consulte [Opções, Editor de Texto, C#, Formatação](/visualstudio/ide/reference/options-text-editor-csharp-formatting).  
  
-   Gravar apenas uma instrução por linha.  
  
-   Gravar apenas uma declaração por linha.  
  
-   Se as linhas de continuação não devem recuar automaticamente, recue-as uma tabulação (quatro espaços).  
  
-   Adicione pelo menos uma linha em branco entre as definições de método e de propriedade.  
  
-   Use parênteses para criar cláusulas em uma expressão aparente, conforme mostrado no código a seguir.  
  
     [!code-cs[csProgGuideCodingConventions#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_2.cs)]  
  
## <a name="commenting-conventions"></a>Comentando Convenções  
  
-   Coloque o comentário em uma linha separada, não no final de uma linha de código.  
  
-   Comece o texto do comentário com uma letra maiúscula.  
  
-   Termine o texto do comentário com um ponto final.  
  
-   Insira um espaço entre o delimitador de comentário (/ /) e o texto do comentário, conforme mostrado no exemplo a seguir.  
  
     [!code-cs[csProgGuideCodingConventions#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_3.cs)]  
  
-   Não crie blocos de asteriscos formatados em torno dos comentários.  
  
## <a name="language-guidelines"></a>Diretrizes de Linguagem  
 As seções a seguir descrevem práticas que a equipe de C# segue para preparar exemplos e amostras do código.  
  
### <a name="string-data-type"></a>Tipo de dados da cadeia de caracteres  
  
-   Use o operador `+` para concatenar cadeias de caracteres curtas, conforme mostrado no código a seguir.  
  
     [!code-cs[csProgGuideCodingConventions#6](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_4.cs)]  
  
-   Para acrescentar cadeias de caracteres em loops, especialmente quando você estiver trabalhando com grandes quantidades de texto, use um objeto <xref:System.Text.StringBuilder>.  
  
     [!code-cs[csProgGuideCodingConventions#7](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_5.cs)]  
  
### <a name="implicitly-typed-local-variables"></a>Variáveis Locais Tipadas Implicitamente  
  
-   Use a [digitação implícita](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) para variáveis locais quando o tipo da variável for óbvio do lado direito da atribuição ou quando o tipo exato não for importante.  
  
     [!code-cs[csProgGuideCodingConventions#8](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_6.cs)]  
  
-   Não use [var](../../../csharp/language-reference/keywords/var.md) quando o tipo não estiver aparente no lado direito da atribuição.  
  
     [!code-cs[csProgGuideCodingConventions#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_7.cs)]  
  
-   Não se baseie no nome da variável para especificar o tipo dela. Ele pode não estar correto.  
  
     [!code-cs[csProgGuideCodingConventions#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_8.cs)]  
  
-   Evite o uso de `var` em vez de [dynamic](../../../csharp/language-reference/keywords/dynamic.md).  
  
-   Use a digitação implícita para determinar o tipo da variável de loop nos loops [for](../../../csharp/language-reference/keywords/for.md) e [foreach](../../../csharp/language-reference/keywords/foreach-in.md).  
  
     O exemplo a seguir usa digitação implícita em uma instrução `for`.  
  
     [!code-cs[csProgGuideCodingConventions#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_9.cs)]  
  
     O exemplo a seguir usa digitação implícita em uma instrução `foreach`.  
  
     [!code-cs[csProgGuideCodingConventions#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_10.cs)]  
  
### <a name="unsigned-data-type"></a>Tipo de Dados Sem Sinal  
  
-   Em geral, use `int` em vez de tipos sem assinatura. O uso de `int` é comum em todo o C#, e é mais fácil interagir com outras bibliotecas ao usar `int`.  
  
### <a name="arrays"></a>Matrizes  
  
-   Use a sintaxe concisa ao inicializar matrizes na linha da declaração.  
  
     [!code-cs[csProgGuideCodingConventions#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_11.cs)]  
  
### <a name="delegates"></a>Delegados  
  
-   Use a sintaxe concisa ao criar instâncias de um tipo delegado.  
  
     [!code-cs[csProgGuideCodingConventions#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_12.cs)]  
  
     [!code-cs[csProgGuideCodingConventions#15](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_13.cs)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a>try-catch e instruções de uso no tratamento de exceção  
  
-   Use uma instrução [try-catch](../../../csharp/language-reference/keywords/try-catch.md) para a maioria da manipulação de exceções.  
  
     [!code-cs[csProgGuideCodingConventions#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_14.cs)]  
  
-   Simplifique o código usando a [instrução using](../../../csharp/language-reference/keywords/using-statement.md) do #C. Se você tiver uma instrução [try-finally](../../../csharp/language-reference/keywords/try-finally.md) na qual o único código do bloco `finally` é uma chamada para o método <xref:System.IDisposable.Dispose%2A>, use, em vez disso, uma instrução `using`.  
  
     [!code-cs[csProgGuideCodingConventions#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_15.cs)]  
  
### <a name="-and-124124-operators"></a>Operadores && e &#124;&#124;  
  
-   Para evitar exceções e aumentar o desempenho ignorando comparações desnecessárias, use [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) em vez de [&](../../../csharp/language-reference/operators/and-operator.md) e [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) em vez de [&#124;](../../../csharp/language-reference/operators/or-operator.md) ao executar comparações, conforme mostrado no exemplo a seguir.  
  
     [!code-cs[csProgGuideCodingConventions#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_16.cs)]  
  
### <a name="new-operator"></a>Operador New  
  
-   Use um formulário conciso de instanciação de objeto com digitação implícita, conforme mostrado na declaração a seguir.  
  
     [!code-cs[csProgGuideCodingConventions#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_17.cs)]  
  
     A linha anterior é equivalente à declaração a seguir.  
  
     [!code-cs[csProgGuideCodingConventions#20](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_18.cs)]  
  
-   Use inicializadores de objeto para simplificar a criação do objeto.  
  
     [!code-cs[csProgGuideCodingConventions#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_19.cs)]  
  
### <a name="event-handling"></a>Tratamento de Evento  
  
-   Se você estiver definindo um manipulador de eventos que não necessita ser removido posteriormente, use uma expressão lambda.  
  
     [!code-cs[csProgGuideCodingConventions#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_20.cs)]  
  
     [!code-cs[csProgGuideCodingConventions#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_21.cs)]  
  
### <a name="static-members"></a>Membros Estáticos  
  
-   Chame membros [estáticos](../../../csharp/language-reference/keywords/static.md) usando o nome de classe: *ClassName.StaticMember*. Essa prática torna o código mais legível, tornando o acesso estático limpo.  Não qualifique um membro estático definido em uma classe base com o nome de uma classe derivada.  Enquanto esse código é compilado, a leitura do código fica incorreta e o código poderá ser danificado no futuro se você adicionar um membro estático com o mesmo nome da classe derivada.  
  
### <a name="linq-queries"></a>Consultas LINQ  
  
-   Use nomes significativos para variáveis de consulta. O exemplo a seguir usa `seattleCustomers` para os clientes que estão localizados em Seattle.  
  
     [!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]  
  
-   Use aliases para se certificar de que os nomes de propriedades de tipos anônimos sejam colocados corretamente em maiúsculas, usando o padrão Pascal-Case.  
  
     [!code-cs[csProgGuideCodingConventions#26](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_23.cs)]  
  
-   Renomeie propriedades quando os nomes de propriedades no resultado forem ambíguos. Por exemplo, se a sua consulta retornar um nome de cliente e uma ID de distribuidor, em vez de deixá-los como `Name` e `ID` no resultado, renomeie-os para esclarecer que `Name` é o nome de um cliente, e `ID` é a identificação de um distribuidor.  
  
     [!code-cs[csProgGuideCodingConventions#27](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_24.cs)]  
  
-   Usa a digitação implícita na declaração de variáveis de consulta e de intervalo.  
  
     [!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]  
  
-   Alinhe cláusulas de consulta na cláusula [from](../../../csharp/language-reference/keywords/from-clause.md), conforme mostrado nos exemplos anteriores.  
  
-   Use cláusulas [where](../../../csharp/language-reference/keywords/where-clause.md) antes de outras cláusulas de consulta para garantir que cláusulas de consulta posteriores operem no conjunto de dados filtrado e reduzido.  
  
     [!code-cs[csProgGuideCodingConventions#29](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_25.cs)]  
  
-   Use várias cláusulas `from` em vez de uma cláusula [join](../../../csharp/language-reference/keywords/join-clause.md) para acessar coleções internas. Por exemplo, cada coleção de objetos `Student` pode conter um conjunto de pontuações no teste. Quando a próxima consulta for executada, ela retorna cada pontuação que seja acima de 90, juntamente com o sobrenome do estudante que recebeu a pontuação.  
  
     [!code-cs[csProgGuideCodingConventions#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_26.cs)]  
  
## <a name="security"></a>Segurança  
 Siga as diretrizes em [Diretrizes de codificação segura](../../../standard/security/secure-coding-guidelines.md).  
  
## <a name="see-also"></a>Consulte também  
 [Convenções de codificação do Visual Basic](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)   
 [Diretrizes de codificação segura](../../../standard/security/secure-coding-guidelines.md)

