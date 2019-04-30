---
title: Recursos do Visual Basic que suportam LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: 155d5c36483accc12d066a5530fea20a563e1498
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61977555"
---
# <a name="visual-basic-features-that-support-linq"></a>Recursos do Visual Basic que suportam LINQ
O nome [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] refere-se à tecnologia no Visual Basic que dá suporte à sintaxe de consulta e outra linguagem constrói diretamente na linguagem. Com [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], você não precisa aprender uma nova linguagem de consulta em relação a uma fonte de dados externa. Você pode consultar em relação aos dados em bancos de dados relacionais, armazenamentos de XML ou objetos usando o Visual Basic. Essa integração de recursos de consulta para o idioma permite a verificação de tempo de compilação para erros de sintaxe e segurança de tipo. Essa integração também garante que você já sabe a maioria dos quais você precisa saber para escrever consultas avançadas e variadas em Visual Basic.  
  
 As seções a seguir descrevem as construções de linguagem que dão suporte a LINQ em detalhes suficientes para que você possa começar a ler a documentação introdutória, exemplos de código e aplicativos de exemplo. Você também pode clicar nos links para localizar explicações mais detalhadas sobre como os recursos de linguagem se unem para habilitar a consulta integrada à linguagem. Um bom lugar para começar é [passo a passo: Escrevendo consultas em Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).  
  
## <a name="query-expressions"></a>Expressões de consulta  
 Expressões de consulta no Visual Basic podem ser expressa em uma sintaxe declarativa semelhante do SQL ou XQuery. Em tempo de compilação, a sintaxe de consulta é convertida em chamadas de método para implementação de um provedor LINQ dos métodos de extensão do operador de consulta padrão. Controle de aplicativos que os operadores de consulta padrão estão no escopo, especificando o namespace apropriado com um `Imports` instrução. Sintaxe para uma expressão de consulta do Visual Basic tem esta aparência:  
  
 [!code-vb[VbLINQVbFeatures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#1)]  
  
 Para obter mais informações, consulte [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="implicitly-typed-variables"></a>Variáveis de tipo implícito  
 Em vez de especificar explicitamente um tipo ao declarar e inicializar uma variável, você pode habilitar o compilador a inferir e atribuir o tipo. Isso é conhecido como *inferência de tipo local*.  
  
 Variáveis cujos tipos são inferidos são fortemente tipadas, como as variáveis cujo tipo você especifica explicitamente. Inferência de tipo local só funciona quando você está definindo uma variável local dentro de um corpo de método. Para obter mais informações, consulte [instrução opção inferir](../../../../visual-basic/language-reference/statements/option-infer-statement.md) e [inferência de tipo Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 O exemplo a seguir ilustra a inferência de tipo local. Para usar este exemplo, você deve definir `Option Infer` para `On`.  
  
 [!code-vb[VbLINQVbFeatures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#2)]  
  
 Inferência de tipo local também torna possível criar tipos anônimos, que são descritos posteriormente nesta seção e são necessários para consultas LINQ.  
  
 No exemplo a seguir LINQ, a inferência de tipo ocorrerá se `Option Infer` seja `On` ou `Off`. Ocorrerá um erro de tempo de compilação se `Option Infer` está `Off` e `Option Strict` é `On`.  
  
 [!code-vb[VbLINQVbFeatures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#3)]  
  
## <a name="object-initializers"></a>Inicializadores de objeto  
 Inicializadores de objeto são usados em expressões de consulta quando você tem que criar um tipo anônimo para manter os resultados de uma consulta. Eles também podem ser usados para inicializar objetos dos tipos nomeados fora de consultas. Usando um inicializador de objeto, você pode inicializar um objeto em uma única linha sem chamar explicitamente um construtor. Supondo que você tenha uma classe chamada `Customer` que tem pública `Name` e `Phone` propriedades, juntamente com outras propriedades, um inicializador de objeto pode ser usado dessa maneira:  
  
 [!code-vb[VbLINQVbFeatures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#4)]  
  
 Para obter mais informações, consulte [inicializadores de objeto: Tipos nomeados e anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="anonymous-types"></a>Tipos anônimos  
 Tipos anônimos fornecem uma maneira conveniente de agrupar temporariamente um conjunto de propriedades em um elemento que você deseja incluir em um resultado de consulta. Isso permite que você escolher qualquer combinação de campos disponíveis na consulta, em qualquer ordem, sem definir um tipo de dados nomeado para o elemento.  
  
 Uma *tipo anônimo* é construído dinamicamente pelo compilador. O nome do tipo é atribuído pelo compilador, e ele poderá ser alterado com cada nova compilação. Portanto, o nome não pode ser usado diretamente. Tipos anônimos são inicializados da seguinte maneira:  
  
 [!code-vb[VbLINQVbFeatures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#5)]  
  
 Para obter mais informações, consulte [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="extension-methods"></a>Métodos de extensão  
 Métodos de extensão permitem adicionar métodos a um tipo de dados ou a interface de fora da definição. Esse recurso permite que você, na verdade, adicionar novos métodos a um tipo existente sem modificar o tipo de fato. Operadores de consulta padrão são um conjunto de métodos de extensão que fornecem [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] funcionalidade de consulta para qualquer tipo que implemente <xref:System.Collections.Generic.IEnumerable%601>. Outras extensões <xref:System.Collections.Generic.IEnumerable%601> incluem <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>, e <xref:System.Linq.Enumerable.Intersect%2A>.  
  
 O método de extensão a seguir adiciona um método de impressão para o <xref:System.String> classe.  
  
 [!code-vb[VbLINQVbFeatures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#6)]  
  
 O método é chamado como um método comum de instância de <xref:System.String>:  
  
 [!code-vb[VbLINQVbFeatures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#7)]  
  
 Para obter mais informações, consulte [Métodos de extensão](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Expressões lambda  
 Uma expressão lambda é uma função sem um nome que calcula e retorna um único valor. Diferentemente das funções nomeadas, uma expressão lambda pode ser definida e executada ao mesmo tempo. O exemplo a seguir exibe 4.  
  
 [!code-vb[VbLINQVbFeatures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#8)]  
  
 Você pode atribuir a definição da expressão lambda para um nome de variável e, em seguida, use o nome para chamar a função. O exemplo a seguir também exibe 4.  
  
 [!code-vb[VbLINQVbFeatures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#12)]  
  
 No [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], expressões lambda são a base de muitos dos operadores de consulta padrão. O compilador cria expressões lambda para capturar os cálculos que são definidos como métodos de consulta fundamentais `Where`, `Select`, `Order By`, `Take While`e outros.  
  
 Por exemplo, o código a seguir define uma consulta que retorna todos os alunos sênior de uma lista de alunos.  
  
 [!code-vb[VbLINQVbFeatures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#9)]  
  
 A definição de consulta é compilada em código que é semelhante ao exemplo a seguir, que usa duas expressões lambda para especificar os argumentos para `Where` e `Select`.  
  
 [!code-vb[VbLINQVbFeatures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#10)]  
  
 Qualquer versão pode ser executada usando um `For Each` loop:  
  
 [!code-vb[VbLINQVbFeatures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#11)]  
  
 Para obter mais informações, consulte [Expressões Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="see-also"></a>Consulte também

- [LINQ (consulta integrada à linguagem) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [LINQ e cadeias de caracteres (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [Instrução Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
