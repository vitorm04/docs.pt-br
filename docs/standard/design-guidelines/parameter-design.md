---
title: Design de parâmetro
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
author: KrzysztofCwalina
ms.openlocfilehash: 28b00f5911bb47536ec44b96f284e47b6c671149
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353735"
---
# <a name="parameter-design"></a>Design de parâmetro
Esta seção fornece diretrizes amplas sobre o design de parâmetros, incluindo seções com diretrizes para verificar argumentos. Além disso, você deve consultar as diretrizes descritas em [parâmetros de nomenclatura](../../../docs/standard/design-guidelines/naming-parameters.md).  
  
 **✓ DO** usar o tipo de parâmetro menos derivado que fornece a funcionalidade exigida pelo membro.  
  
 Por exemplo, suponha que você queira criar um método que enumere uma coleção e imprima cada item no console. Esse método deve levar <xref:System.Collections.IEnumerable> como o parâmetro, não <xref:System.Collections.ArrayList> ou <xref:System.Collections.IList>, por exemplo.  
  
 **X DO NOT** usar parâmetros reservados.  
  
 Se mais entradas para um membro forem necessárias em alguma versão futura, uma nova sobrecarga poderá ser adicionada.  
  
 **X DO NOT** publicamente expor métodos que usam ponteiros, matrizes de ponteiros ou matrizes multidimensionais como parâmetros.  
  
 Ponteiros e matrizes multidimensionais são relativamente difíceis de usar corretamente. Em quase todos os casos, as APIs podem ser reprojetadas para evitar a criação desses tipos como parâmetros.  
  
 **✓ DO** colocar todos os `out` parâmetros após todos o por valor e `ref` parâmetros (excluindo matrizes de parâmetros), mesmo se ele resulta em uma inconsistência no parâmetro ordenação entre sobrecargas (consulte [membro Sobrecarga](../../../docs/standard/design-guidelines/member-overloading.md)).  
  
 Os parâmetros `out` podem ser vistos como valores de retorno extras, e agrupá-los juntos torna a assinatura do método mais fácil de entender.  
  
 **✓ DO** seja consistente em nomes de parâmetros ao substituir membros ou implementar membros de interface.  
  
 Isso comunica melhor a relação entre os métodos.  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a>Escolhendo entre parâmetros de enumeração e boolianos  
 **✓ DO** usar enums se um membro tivesse dois ou mais parâmetros booleanos.  
  
 **X DO NOT** usar valores booleanos, a menos que você tiver certeza absoluta nunca haverá a necessidade de mais de dois valores.  
  
 As enumerações oferecem algum espaço para a adição futura de valores, mas você deve estar ciente de todas as implicações da adição de valores a enums, que são descritas em [design de enumeração](../../../docs/standard/design-guidelines/enum.md).  
  
 **✓ CONSIDER** usando boolianos para parâmetros de construtor que são valores de dois estados realmente e são usados simplesmente para inicializar propriedades Boolianas.  
  
### <a name="validating-arguments"></a>Validando argumentos  
 **✓ DO** validar argumentos passados para membros públicos, protegidos ou implementados explicitamente. Gere <xref:System.ArgumentException?displayProperty=nameWithType>, ou uma de suas subclasses, se a validação falhar.  
  
 Observe que a validação real não precisa necessariamente acontecer no próprio membro público ou protegido. Isso pode acontecer em um nível inferior em alguma rotina privada ou interna. O ponto principal é que toda a área de superfície exposta aos usuários finais verifica os argumentos.  
  
 **✓ DO** gerar <xref:System.ArgumentNullException> se um argumento nulo é passado e o membro não oferece suporte a argumentos nulos.  
  
 **✓ DO** validar parâmetros de enum.  
  
 Não assuma que os argumentos de enumeração estarão no intervalo definido pela enumeração. O CLR permite a conversão de qualquer valor inteiro em um valor de enumeração, mesmo se o valor não estiver definido na enumeração.  
  
 **X DO NOT** usar <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> para o intervalo de enum verifica.  
  
 **✓ DO** Lembre-se de que os argumentos mutáveis podem ter alterado depois que eles foram validados.  
  
 Se o membro for sensível à segurança, você será incentivado a fazer uma cópia e, em seguida, validar e processar o argumento.  
  
### <a name="parameter-passing"></a>Passagem de parâmetro  
 Da perspectiva de um designer de estrutura, há três grupos principais de parâmetros: parâmetros por valor, parâmetros `ref` e parâmetros de `out`.  
  
 Quando um argumento é passado por um parâmetro por valor, o membro recebe uma cópia do argumento real passado. Se o argumento for um tipo de valor, uma cópia do argumento será colocada na pilha. Se o argumento for um tipo de referência, uma cópia da referência será colocada na pilha. As C#linguagens CLR mais populares, como, VB.net e C++, por padrão, passar parâmetros por valor.  
  
 Quando um argumento é passado através de um parâmetro `ref`, o membro recebe uma referência para o argumento real passado. Se o argumento for um tipo de valor, uma referência ao argumento será colocada na pilha. Se o argumento for um tipo de referência, uma referência à referência será colocada na pilha. parâmetros `Ref` podem ser usados para permitir que o membro modifique argumentos passados pelo chamador.  
  
 os parâmetros `Out` são semelhantes aos parâmetros `ref`, com algumas pequenas diferenças. O parâmetro é inicialmente considerado não atribuído e não pode ser lido no corpo do membro antes de ser atribuído a um valor. Além disso, o parâmetro deve ser atribuído a um valor antes que o membro seja retornado.  
  
 **X AVOID** usando `out` ou `ref` parâmetros.  
  
 Usar parâmetros `out` ou `ref` requer experiência com ponteiros, compreendendo como tipos de valor e tipos de referência diferem e manipulando métodos com vários valores de retorno. Além disso, a diferença `out` entre `ref` os parâmetros e não é amplamente compreendida. Os arquitetos de estrutura que projetam para um público geral não devem esperar que os usuários façam o mestre de trabalho com parâmetros `out` ou `ref`.  
  
 **X DO NOT** passar tipos de referência por referência.  
  
 Há algumas exceções limitadas à regra, como um método que pode ser usado para alternar referências.  
  
### <a name="members-with-variable-number-of-parameters"></a>Membros com número variável de parâmetros  
 Os membros que podem obter um número variável de argumentos são expressos fornecendo um parâmetro de matriz. Por exemplo, <xref:System.String> fornece o seguinte método:  
  
```csharp  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 Em seguida, um usuário pode chamar o método <xref:System.String.Format%2A?displayProperty=nameWithType>, da seguinte maneira:  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 A adição C# da palavra-chave params a um parâmetro de matriz altera o parâmetro para o chamado parâmetro de matriz params e fornece um atalho para a criação de uma matriz temporária.  
  
```csharp  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 Fazer isso permite que o usuário chame o método passando os elementos da matriz diretamente na lista de argumentos.  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 Observe que a palavra-chave params pode ser adicionada somente ao último parâmetro na lista de parâmetros.  
  
 **✓ CONSIDER** adicionando a palavra-chave params para parâmetros de matriz, se você espera que os usuários finais para transmitir matrizes com um pequeno número de elementos. Se for esperado que muitos elementos sejam passados em cenários comuns, os usuários provavelmente não passarão esses elementos embutidos de qualquer forma e, portanto, a palavra-chave params não será necessária.  
  
 **X AVOID** usando matrizes de parâmetros se o chamador quase sempre deve ter a entrada já em uma matriz.  
  
 Por exemplo, os membros com parâmetros de matriz de bytes quase nunca seriam chamados passando bytes individuais. Por esse motivo, os parâmetros de matriz de bytes no .NET Framework não usam a palavra-chave params.  
  
 **X DO NOT** usar matrizes de parâmetros, se a matriz é modificada pelo membro levando o parâmetro de matriz de parâmetros.  
  
 Por causa do fato de que muitos compiladores transformam os argumentos para o membro em uma matriz temporária no site de chamada, a matriz pode ser um objeto temporário e, portanto, qualquer modificação na matriz será perdida.  
  
 **✓ CONSIDER** usando a palavra-chave params em uma sobrecarga simple, mesmo se uma sobrecarga mais complexa não pode usá-lo.  
  
 Pergunte-se se os usuários teriam valor com a matriz params em uma sobrecarga, mesmo que não estivesse em todas as sobrecargas.  
  
 **✓ DO** tente parâmetros de ordem para que seja possível usar a palavra-chave params.  
  
 **✓ CONSIDER** fornecendo sobrecargas especiais e caminhos de código para chamadas com um pequeno número de argumentos nas APIs de desempenho extremamente sensíveis.  
  
 Isso possibilita evitar a criação de objetos de matriz quando a API é chamada com um pequeno número de argumentos. Formate os nomes dos parâmetros por meio de uma forma singular do parâmetro de matriz e adicionando um sufixo numérico.  
  
 Você só deve fazer isso se for para o caso especial do caminho de código inteiro, não apenas criar uma matriz e chamar o método mais geral.  
  
 **✓ DO** Lembre-se de que null pode ser passado como um argumento de matriz de parâmetros.  
  
 Você deve validar que a matriz não é nula antes do processamento.  
  
 **X DO NOT** usar o `varargs` métodos, também conhecidos como o botão de reticências.  
  
 Algumas linguagens CLR, como C++, oferecem suporte a uma convenção alternativa para passar listas de parâmetros variáveis chamadas de métodos `varargs`. A Convenção não deve ser usada em estruturas, pois não é compatível com CLS.  
  
### <a name="pointer-parameters"></a>Parâmetros do ponteiro  
 Em geral, os ponteiros não devem aparecer na área de superfície pública de uma estrutura de código gerenciada bem projetada. Na maioria das vezes, os ponteiros devem ser encapsulados. No entanto, em alguns casos, os ponteiros são necessários para motivos de interoperabilidade e o uso de ponteiros nesses casos é apropriado.  
  
 **✓ DO** fornecem uma alternativa para qualquer membro que usa um argumento de ponteiro, como ponteiros não são compatíveis com CLS.  
  
 **X AVOID** fazendo caro argumento verificação de argumentos de ponteiro.  
  
 **✓ DO** convenções comuns relacionados ao ponteiro durante a criação de membros com ponteiros.  
  
 Por exemplo, não há necessidade de passar o índice inicial, porque a aritmética simples de ponteiro pode ser usada para atingir o mesmo resultado.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reprinted por permissão do Pearson Education, Inc. de diretrizes de design [Framework: Convenções, idiomas e padrões para bibliotecas .NET reutilizáveis, 2ª edição @ no__t-0 por Krzysztof Cwalina e Brad Abrams, publicadas em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
