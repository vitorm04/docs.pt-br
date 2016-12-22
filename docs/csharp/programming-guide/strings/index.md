---
title: "Cadeias de caracteres (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Linguagem C#, cadeias de caracteres"
  - "cadeias de caracteres [C#]"
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
caps.latest.revision: 41
caps.handback.revision: 41
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Cadeias de caracteres (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma seqüência de caracteres é um objeto do tipo <xref:System.String> cujo valor é texto.  Internamente, o texto é armazenado como uma coleção seqüencial de somente leitura de <xref:System.Char> objetos.  Não há nenhum caractere nulo de terminação no final de uma seqüência de C\#; Portanto, uma seqüência de caracteres C\# pode conter qualquer número de caracteres de nulos incorporados \('\\0'\).  O <xref:System.String.Length%2A> propriedade de uma seqüência de caracteres representa o número de `Char` objetos que ele contém, não o número de caracteres Unicode.  Para acessar os pontos de código Unicode individuais em uma seqüência de caracteres, use o <xref:System.Globalization.StringInfo> objeto.  
  
## seqüência de caracteres vs.System. String  
 No C\#, o `string` palavra\-chave é um alias para <xref:System.String>.  Portanto, `String` e `string` são equivalentes e você pode usar qualquer convenção de nomenclatura que você preferir.  O `String` classe fornece vários métodos para criação com segurança, manipulação e comparação de seqüências de caracteres.  Além disso, a linguagem C\# sobrecarrega alguns operadores para simplificar as operações mais comuns com strings.  Para obter mais informações sobre a palavra\-chave, consulte [cadeia de caracteres](../../../csharp/language-reference/keywords/string.md).  Para obter mais informações sobre o tipo e seus métodos, consulte <xref:System.String>.  
  
## Declarar e inicializar as seqüências de caracteres  
 Você pode declarar e inicializar as seqüências de caracteres de várias formas, conforme o exemplo seguinte:  
  
 [!code-cs[csProgGuideStrings#1](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_1.cs)]  
  
 Observe que você não use o  [nova](../../../visual-basic/language-reference/operators/new-operator.md) operador para criar um objeto de seqüência de caracteres, exceto quando Inicializando a seqüência de caracteres com uma matriz de caracteres.  
  
 Inicializar uma seqüência de caracteres com o <xref:System.String.Empty> para criar um novo valor da constante <xref:System.String> objeto cuja seqüência é de comprimento zero.  A representação literal de uma string de comprimento zero é "".  Inicializando cadeias de caracteres com o <xref:System.String.Empty> valor em vez de  [Nulo](../../../csharp/language-reference/keywords/null.md), você pode reduzir as chances de um <xref:System.NullReferenceException> que ocorrem.  Use estática <xref:System.String.IsNullOrEmpty%28System.String%29> método para verificar o valor de uma seqüência de caracteres antes de você tenta acessá\-la.  
  
## Imutabilidade de objetos String  
 Objetos String são  *imutáveis*: não pode ser alterados depois que eles foram criados.  Todas as <xref:System.String> C\# operadores que aparecem para modificar uma seqüência de caracteres e métodos, na verdade, retornam os resultados em um novo objeto de seqüência de caracteres.  No exemplo a seguir, quando o conteúdo de `s1` e `s2` são concatenados para formar uma única cadeia de caracteres, as duas seqüências de caracteres originais são modificadas.  O `+=` operador cria uma nova seqüência de caracteres que contém o conteúdo combinado.  Esse novo objeto é atribuído à variável `s1`e o objeto original que foi atribuído a `s1` é liberada para coleta de lixo, porque nenhuma outra variável contém uma referência a ele.  
  
 [!code-cs[csProgGuideStrings#2](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_2.cs)]  
  
 Como uma seqüência de caracteres "modificação" é realmente uma nova criação de seqüência de caracteres, você deve usar o cuidado ao criar referências para seqüências de caracteres.  Se você cria uma referência a uma seqüência de caracteres e "modificar", em seguida, a seqüência de caracteres original, continuará a referência apontar para o objeto original em vez de um novo objeto que foi criado quando a seqüência de caracteres foi modificada.  O código a seguir ilustra esse comportamento:  
  
 [!code-cs[csProgGuideStrings#25](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_3.cs)]  
  
 Para obter mais informações sobre como criar novas seqüências de caracteres que sejam baseiam em modificações como pesquisar e substituir operações em seqüência de caracteres original, consulte [Como modificar o conteúdo de uma cadeia de caracteres](../../../csharp/programming-guide/strings/how-to-modify-string-contents.md).  
  
## Literais de seqüência regular e Verbatim  
 Use literais de seqüência de caracteres normal quando você deve incorporar os caracteres de escape fornecidos pela C\#, conforme mostrado no exemplo a seguir:  
  
 [!code-cs[csProgGuideStrings#3](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_4.cs)]  
  
 Use seqüências de caracteres verbatim para conveniência e melhor legibilidade, quando o texto de seqüência de caracteres contém caracteres de barra invertida, por exemplo, em caminhos de arquivo.  Como seqüências de caracteres verbatim preservar os caracteres de nova linha como parte do texto cadeia de caracteres, pode ser usados para inicializar as seqüências de caracteres de várias linhas.  Use aspas duplas para incorporar uma marca de aspas dentro de uma seqüência de caracteres verbatim.  O exemplo a seguir mostra alguns usos comuns para cadeias de caracteres verbatim:  
  
 [!code-cs[csProgGuideStrings#4](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_5.cs)]  
  
## Seqüências de Escape de string  
  
|Seqüência de escape|Nome do caractere|Codificação Unicode|  
|-------------------------|-----------------------|-------------------------|  
|\\'|Aspa simples|0x0027|  
|\\"|Aspas duplas|0x0022|  
|\\\\|Barra invertida|0x005C|  
|\\0|Null|0x0000|  
|\\a|Alertar|0x0007|  
|\\b|BACKSPACE|0x0008|  
|\\f|Avanço de página|0x000C|  
|\\n|Nova linha|0x000A|  
|\\r|Retorno de carro|0x000D|  
|\\t|Guia horizontal|0x0009|  
|\\U|Seqüência de escape do Unicode para pares substitutos.|\\Unnnnnnnn|  
|\\u|Seqüência de escape do Unicode|\\u0041 \= "A"|  
|\\v|Tabulação vertical|0x000B|  
|\\x|Seqüência de escape Unicode semelhante a "\\u", exceto com comprimento variável.|\\x0041 \= "A"|  
  
> [!NOTE]
>  Em tempo de compilação, seqüências de caracteres verbatim são convertidos em cadeias de caracteres comuns com as mesmas seqüências de escape.  Portanto, se você exibir uma seqüência de caracteres verbatim na janela de inspeção de variáveis do depurador, você verá os caracteres de escape que foram adicionados pelo compilador, não a versão verbatim do seu código fonte.  Por exemplo, a seqüência de caracteres verbatim @ "C:\\files.txt" será exibido na janela watch, como "C:\\\\files.txt".  
  
## Seqüências de caracteres de formato  
 Uma seqüência de formato é uma seqüência de caracteres cujo conteúdo pode ser determinado dinamicamente no tempo de execução.  Você cria uma seqüência de caracteres de formato usando estática <xref:System.String.Format%2A> método e a incorporação de espaços reservados chaves serão substituídos por outros valores em tempo de execução.  O exemplo a seguir usa uma seqüência de caracteres de formato para gerar o resultado de cada iteração de um loop:  
  
 [!code-cs[csProgGuideStrings#26](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_6.cs)]  
  
 Uma sobrecarga da <xref:System.Console.WriteLine%2A> método usa uma seqüência de caracteres de formato como um parâmetro.  Portanto, você pode incorporar apenas uma seqüência de caracteres de formato literal sem uma chamada explícita para o método.  No entanto, se você usar o <xref:System.Diagnostics.Trace.WriteLine%2A> método para exibir a saída de depuração na Visual Studio  **saída** janela, você precisa chamar explicitamente o <xref:System.String.Format%2A> método porque <xref:System.Diagnostics.Trace.WriteLine%2A> só aceita uma seqüência de caracteres, não é uma seqüência de formato.  Para obter mais informações sobre seqüências de caracteres de formato, consulte [Formatando tipos](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md).  
  
## Substrings  
 Uma subseqüência de caracteres é qualquer seqüência de caracteres que está contida em uma seqüência de caracteres.  Use o <xref:System.String.Substring%2A> método para criar uma nova seqüência de caracteres de uma parte da seqüência de caracteres original.  Você pode procurar por uma ou mais ocorrências de uma substring usando o <xref:System.String.IndexOf%2A> método.  Use o <xref:System.String.Replace%2A> método para substituir todas as ocorrências de uma subseqüência especificada com uma nova seqüência.  Como o <xref:System.String.Substring%2A> método, <xref:System.String.Replace%2A> , na verdade, retorna uma nova seqüência de caracteres e não modifica a seqüência de caracteres original.  Para obter mais informações, consulte [Como pesquisar cadeias de caracteres usando métodos de cadeia de caracteres](../../../csharp/programming-guide/strings/how-to-search-strings-using-string-methods.md) e [Como modificar o conteúdo de uma cadeia de caracteres](../../../csharp/programming-guide/strings/how-to-modify-string-contents.md).  
  
 [!code-cs[csProgGuideStrings#7](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_7.cs)]  
  
## Acessando caracteres individuais  
 Você pode usar a notação de matriz com um valor de índice para adquirir acesso somente leitura a caracteres individuais, como no exemplo a seguir:  
  
 [!code-cs[csProgGuideStrings#9](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_8.cs)]  
  
 Se a <xref:System.String> métodos não fornecem a funcionalidade que você deve ter para modificar os caracteres individuais em uma seqüência de caracteres, você pode usar um <xref:System.Text.StringBuilder> o objeto para modificar os caracteres individuais "in\-loco" e crie uma nova seqüência de caracteres para armazenar os resultados usando o <xref:System.Text.StringBuilder> métodos.  No exemplo a seguir, suponha que você deve modificar a seqüência de caracteres original de uma determinada maneira e armazenar os resultados para uso futuro:  
  
 [!code-cs[csProgGuideStrings#8](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_9.cs)]  
  
## Seqüências de caracteres nulas e seqüências de caracteres vazias  
 Uma seqüência vazia é uma instância de um <xref:System.String?displayProperty=fullName> o objeto que contém zero caracteres.  Cadeias de caracteres vazias são usadas com freqüência em vários cenários de programação para representar um campo de texto em branco.  Você pode chamar métodos em cadeias de caracteres vazias, porque elas são válidas <xref:System.String?displayProperty=fullName> objetos.  Cadeias de caracteres vazias são inicializadas da seguinte maneira:  
  
```  
string s = String.Empty;  
```  
  
 Por outro lado, uma seqüência nula não se refere a uma instância de um <xref:System.String?displayProperty=fullName> objeto e qualquer tentativa de chamar um método em uma seqüência nula faz com que uma <xref:System.NullReferenceException>.  No entanto, você pode usar seqüências de caracteres nulas em concatenação e as operações de comparação com outras seqüências de caracteres.  Os exemplos a seguir ilustram alguns casos em que uma referência a uma seqüência nula faz e não faz com que uma exceção seja lançada:  
  
 [!code-cs[csProgGuideStrings#27](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_10.cs)]  
  
## Usando o StringBuilder para rápida criação de seqüência de caracteres  
 Operações em cadeia de caracteres.NET são altamente otimizados e na maioria dos casos não afeta o desempenho significativamente.  No entanto, em alguns cenários, como loops rígidos que estiverem executando várias centenas ou milhares de vezes, as operações de cadeia de caracteres podem afetar o desempenho.  O <xref:System.Text.StringBuilder> classe cria um buffer de seqüência de caracteres que oferece melhor desempenho se seu programa executar várias manipulações de seqüência de caracteres.  O <xref:System.Text.StringBuilder> seqüência de caracteres também permite que você reatribuir caracteres individuais, algo a seqüência de caracteres interna não oferece suporte a tipo de dados.  Esse código, por exemplo, altera o conteúdo de uma seqüência de caracteres sem criar uma nova seqüência de caracteres:  
  
 [!code-cs[csProgGuideStrings#20](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_11.cs)]  
  
 Neste exemplo, um <xref:System.Text.StringBuilder> objeto é usado para criar uma seqüência de caracteres a partir de um conjunto de tipos numéricos:  
  
 [!code-cs[csProgGuideStrings#15](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_12.cs)]  
  
## Seqüências de caracteres, os métodos de extensão e LINQ  
 Porque o <xref:System.String> digite implementa <xref:System.Collections.Generic.IEnumerable%601>, você pode usar os métodos de extensão definidos na <xref:System.Linq.Enumerable> classe em cadeias de caracteres.  Para evitar confusão visual, esses métodos são excluídos do IntelliSense para o <xref:System.String> tipo, mas eles estão disponíveis de Todavia.  Você também pode usar [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] expressões em cadeias de caracteres de consulta.  Para obter mais informações, consulte [LINQ e cadeias de caracteres](../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md).  
  
## Tópicos relacionados  
  
|Tópico|Descrição|  
|------------|---------------|  
|[Como modificar o conteúdo de uma cadeia de caracteres](../../../csharp/programming-guide/strings/how-to-modify-string-contents.md)|Fornece um exemplo de código que ilustra como modificar o conteúdo de seqüências de caracteres.|  
|[Como concatenar várias cadeias de caracteres](../Topic/How%20to:%20Concatenate%20Multiple%20Strings%20\(C%23%20Programming%20Guide\).md)|Ilustra como usar o `+` operador e o `Stringbuilder` classe para ingressar em seqüências de caracteres juntos em tempo de compilação e tempo de execução.|  
|[Como comparar cadeias de caracteres](../Topic/How%20to:%20Compare%20Strings%20\(C%23%20Programming%20Guide\).md)|Mostra como executar o ordinais comparações de seqüências de caracteres.|  
|[Como: analisar cadeias de caracteres usando split ](../Topic/How%20to:%20Parse%20Strings%20Using%20String.Split%20\(C%23%20Programming%20Guide\).md)|Contém um exemplo de código ilustra como usar o `String.Split` método para analisar cadeias de caracteres.|  
|[Como pesquisar cadeias de caracteres usando métodos de cadeia de caracteres](../../../csharp/programming-guide/strings/how-to-search-strings-using-string-methods.md)|Explica como usar métodos específicos para pesquisar seqüências de caracteres.|  
|[Como pesquisar cadeias de caracteres usando expressões regulares](../../../csharp/programming-guide/strings/how-to-search-strings-using-regular-expressions.md)|Explica como usar expressões regulares para pesquisar seqüências de caracteres.|  
|[Como determinar se uma cadeia de caracteres representa um valor numérico](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)|Mostra como analisar com segurança uma seqüência de caracteres para ver se ele tem um valor numérico válido.|  
|[Como converter uma cadeia de caracteres em um DateTime](../../../csharp/programming-guide/strings/how-to-convert-a-string-to-a-datetime.md)|Mostra como converter uma seqüência de caracteres como "24\/01\/2008" para um <xref:System.DateTime?displayProperty=fullName> objeto.|  
|[Operações básicas de cadeias de caracteres](../Topic/Basic%20String%20Operations%20in%20the%20.NET%20Framework.md)|Fornece links para tópicos que usam <xref:System.String?displayProperty=fullName> e <xref:System.Text.StringBuilder?displayProperty=fullName> métodos para executar operações básicas de seqüência de caracteres.|  
|[Analisando cadeias de caracteres](../Topic/Parsing%20Strings%20in%20the%20.NET%20Framework.md)|Descreve como inserir caracteres ou espaços vazios em uma sequência de caracteres.|  
|[Comparando cadeias de caracteres](../Topic/Comparing%20Strings%20in%20the%20.NET%20Framework.md)|Inclui informações sobre como comparar seqüências de caracteres e fornece exemplos em C\# e Visual Basic.|  
|[Usando a classe StringBuilder](../Topic/Using%20the%20StringBuilder%20Class%20in%20the%20.NET%20Framework.md)|Descreve como criar e modificar objetos string dinâmico usando o <xref:System.Text.StringBuilder> classe.|  
|[LINQ e cadeias de caracteres](../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)|Fornece informações sobre como executar várias operações de cadeia de caracteres usando consultas LINQ.|  
|[Guia de Programação em C\#](../../../csharp/programming-guide/index.md)|Fornece links para tópicos que explicam as construções de programação em C\#.|  
  
## Capítulo do livro em destaque  
 [Mais informações sobre variáveis de](http://go.microsoft.com/fwlink/?LinkId=221230) na [início 2010 do Visual C\#](http://go.microsoft.com/fwlink/?LinkId=221214)