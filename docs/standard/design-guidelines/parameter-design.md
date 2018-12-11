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
ms.openlocfilehash: a639e1389d0771dfcb5635b7d78982150b684fd3
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150798"
---
# <a name="parameter-design"></a>Design de parâmetro
Esta seção fornece diretrizes amplas sobre design de parâmetro, incluindo seções com as diretrizes para a verificação de argumentos. Além disso, você deve consultar as diretrizes descritas em [parâmetros de nomeação](../../../docs/standard/design-guidelines/naming-parameters.md).  
  
 **✓ DO** usar o tipo de parâmetro menos derivado que fornece a funcionalidade exigida pelo membro.  
  
 Por exemplo, suponha que você deseja criar um método que enumera uma coleção e imprime a cada item no console. Esse tipo de método deve levar <xref:System.Collections.IEnumerable> como o parâmetro, não <xref:System.Collections.ArrayList> ou <xref:System.Collections.IList>, por exemplo.  
  
 **X DO NOT** usar parâmetros reservados.  
  
 Se mais entradas para um membro é necessária em qualquer versão futura, uma nova sobrecarga pode ser adicionada.  
  
 **X DO NOT** publicamente expor métodos que usam ponteiros, matrizes de ponteiros ou matrizes multidimensionais como parâmetros.  
  
 Ponteiros e matrizes multidimensionais são relativamente difícil de usar adequadamente. Quase todos os casos, as APIs pode ser reprojetadas para evitar colocar esses tipos como parâmetros.  
  
 **✓ DO** colocar todos os `out` parâmetros após todos o por valor e `ref` parâmetros (excluindo matrizes de parâmetros), mesmo se ele resulta em uma inconsistência no parâmetro ordenação entre sobrecargas (consulte [membro Sobrecarga](../../../docs/standard/design-guidelines/member-overloading.md)).  
  
 O `out` parâmetros podem ser vistos como valores de retorno extra e agrupando-os torna mais fácil de entender a assinatura do método.  
  
 **✓ DO** seja consistente em nomes de parâmetros ao substituir membros ou implementar membros de interface.  
  
 Isso se comunica melhor a relação entre os métodos.  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a>Escolhendo entre o Enum e parâmetros booleanos  
 **✓ DO** usar enums se um membro tivesse dois ou mais parâmetros booleanos.  
  
 **X DO NOT** usar valores booleanos, a menos que você tiver certeza absoluta nunca haverá a necessidade de mais de dois valores.  
  
 Enums dão espaço para futura inclusão dos valores, mas você deve estar ciente das implicações de adicionar valores a enums, que são descritos em [Design de enumeração](../../../docs/standard/design-guidelines/enum.md).  
  
 **✓ CONSIDER** usando boolianos para parâmetros de construtor que são valores de dois estados realmente e são usados simplesmente para inicializar propriedades Boolianas.  
  
### <a name="validating-arguments"></a>Validando argumentos  
 **✓ DO** validar argumentos passados para membros públicos, protegidos ou implementados explicitamente. Lançar <xref:System.ArgumentException?displayProperty=nameWithType>, ou uma de suas subclasses, se a validação falhar.  
  
 Observe que a validação real não necessariamente precisa acontecer no membro público ou protegido em si. Isso poderia acontecer em um nível inferior em alguma rotina privado ou interno. O ponto principal é que a área da superfície inteira que é exposta aos usuários finais verifica os argumentos.  
  
 **✓ DO** gerar <xref:System.ArgumentNullException> se um argumento nulo é passado e o membro não oferece suporte a argumentos nulos.  
  
 **✓ DO** validar parâmetros de enum.  
  
 Não suponha enum argumentos serão no intervalo definido pela enumeração. O CLR permite converter qualquer valor inteiro em um valor de enumeração, mesmo se o valor não está definido na enumeração.  
  
 **X DO NOT** usar <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> para o intervalo de enum verifica.  
  
 **✓ DO** Lembre-se de que os argumentos mutáveis podem ter alterado depois que eles foram validados.  
  
 Se o membro é sensível à segurança, você é incentivado a fazer uma cópia e, em seguida, validar e processar o argumento.  
  
### <a name="parameter-passing"></a>Passagem de parâmetro  
 Da perspectiva de um designer de estrutura, há três grupos principais de parâmetros: parâmetros de, pelo valor `ref` parâmetros, e `out` parâmetros.  
  
 Quando um argumento é passado por meio de um parâmetro por valor, o membro recebe uma cópia do argumento real passado. Se o argumento for um tipo de valor, uma cópia do argumento é colocada na pilha. Se o argumento for um tipo de referência, uma cópia da referência será colocada na pilha. Linguagens mais populares de CLR, como c#, VB.NET e C++, padrão para passar parâmetros por valor.  
  
 Quando um argumento é passado por meio de um `ref` parâmetro, o membro recebe uma referência para o argumento real passado. Se o argumento for um tipo de valor, uma referência para o argumento é colocada na pilha. Se o argumento for um tipo de referência, uma referência para a referência será colocada na pilha. `Ref` parâmetros podem ser usados para permitir que o membro modificar os argumentos passados pelo chamador.  
  
 `Out` parâmetros são semelhantes aos `ref` parâmetros, com algumas pequenas diferenças. O parâmetro inicialmente é considerado não atribuídos e não pode ser lido no corpo do membro antes que ele seja atribuído a algum valor. Além disso, o parâmetro deve ser atribuído a algum valor antes de retorna o membro.  
  
 **X AVOID** usando `out` ou `ref` parâmetros.  
  
 Usando o `out` ou `ref` parâmetros requer experiência com ponteiros, compreensão das diferem entre tipos de valor e tipos de referência e métodos de tratamento com vários valores de retorno. Além disso, a diferença entre `out` e `ref` parâmetros não é amplamente compreendida. Arquitetos de estrutura criando para o público em geral não devem esperar que os usuários dominem o trabalho com `out` ou `ref` parâmetros.  
  
 **X DO NOT** passar tipos de referência por referência.  
  
 Há algumas exceções limitadas para a regra, como um método que pode ser usado para trocar as referências.  
  
### <a name="members-with-variable-number-of-parameters"></a>Membros com um número variável de parâmetros  
 Os membros que podem levar a um número variável de argumentos são expressos, fornecendo um parâmetro de matriz. Por exemplo, <xref:System.String> fornece o seguinte método:  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 Um usuário pode, em seguida, chamar o <xref:System.String.Format%2A?displayProperty=nameWithType> método, da seguinte maneira:  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 Adicionando a palavra-chave c# param. autom a um parâmetro de matriz altera o parâmetro a um parâmetro de matriz params de chamada e fornece um atalho para a criação de uma matriz temporária.  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 Isso permite que o usuário chamar o método, passando os elementos da matriz diretamente na lista de argumentos.  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 Observe que a palavra-chave params pode ser adicionada somente para o último parâmetro na lista de parâmetros.  
  
 **✓ CONSIDER** adicionando a palavra-chave params para parâmetros de matriz, se você espera que os usuários finais para transmitir matrizes com um pequeno número de elementos. Se for esperado que muitos elementos serão passados em comum cenários, os usuários provavelmente não irá passar esses elementos embutidos de qualquer forma e, assim a palavra-chave params não é necessária.  
  
 **X AVOID** usando matrizes de parâmetros se o chamador quase sempre deve ter a entrada já em uma matriz.  
  
 Por exemplo, membros com os parâmetros de matriz de bytes seriam quase nunca ser chamados, passando bytes individuais. Por esse motivo, os parâmetros de matriz de bytes no .NET Framework não usam a palavra-chave params.  
  
 **X DO NOT** usar matrizes de parâmetros, se a matriz é modificada pelo membro levando o parâmetro de matriz de parâmetros.  
  
 Devido ao fato de que muitos compiladores transformar os argumentos para o membro em uma matriz temporária no site de chamada, a matriz pode ser um objeto temporário e, portanto, qualquer modificação para a matriz serão perdidas.  
  
 **✓ CONSIDER** usando a palavra-chave params em uma sobrecarga simple, mesmo se uma sobrecarga mais complexa não pode usá-lo.  
  
 Se pergunte se os usuários seriam valor com a matriz de parâmetros em uma sobrecarga, mesmo se ele não estava em todas as sobrecargas.  
  
 **✓ DO** tente parâmetros de ordem para que seja possível usar a palavra-chave params.  
  
 **✓ CONSIDER** fornecendo sobrecargas especiais e caminhos de código para chamadas com um pequeno número de argumentos nas APIs de desempenho extremamente sensíveis.  
  
 Isso torna possível para evitar a criação de objetos de matriz quando a API é chamada com um pequeno número de argumentos. Os nomes dos parâmetros de formulário utilizando uma forma singular do parâmetro de matriz e adicionando um sufixo numérico.  
  
 Você deve fazer isso somente se você for para casos especiais o caminho de código inteiro, não apenas criar uma matriz e chame o método mais geral.  
  
 **✓ DO** Lembre-se de que null pode ser passado como um argumento de matriz de parâmetros.  
  
 Você deve validar que a matriz não é nula antes do processamento.  
  
 **X DO NOT** usar o `varargs` métodos, também conhecidos como o botão de reticências.  
  
 Algumas linguagens do CLR, como C++, dar suporte a uma convenção alternativa para a passagem de listas de parâmetro de variável chamadas `varargs` métodos. A convenção não deve ser usada em estruturas, porque ele não é compatível com CLS.  
  
### <a name="pointer-parameters"></a>Parâmetros de ponteiro  
 Em geral, os ponteiros não devem aparecer na área de superfície pública de uma estrutura de código gerenciado bem projetado. Na maioria das vezes, os ponteiros devem ser encapsulados. No entanto, em alguns casos, ponteiros são necessários por motivos de interoperabilidade e o uso de ponteiros em tais casos é apropriado.  
  
 **✓ DO** fornecem uma alternativa para qualquer membro que usa um argumento de ponteiro, como ponteiros não são compatíveis com CLS.  
  
 **X AVOID** fazendo caro argumento verificação de argumentos de ponteiro.  
  
 **✓ DO** convenções comuns relacionados ao ponteiro durante a criação de membros com ponteiros.  
  
 Por exemplo, não é necessário para passar o índice inicial, pois a aritmética de ponteiro simple pode ser usada para alcançar o mesmo resultado.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)  
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
