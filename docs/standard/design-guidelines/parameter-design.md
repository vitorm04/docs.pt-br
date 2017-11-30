---
title: "Design de parâmetro"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7d49c4263517830f46b1416684c7d9b874cda4db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="parameter-design"></a>Design de parâmetro
Esta seção fornece diretrizes gerais sobre o design de parâmetro, incluindo seções com as diretrizes para a verificação de argumentos. Além disso, consulte as diretrizes descritas em [parâmetros de nomeação de](../../../docs/standard/design-guidelines/naming-parameters.md).  
  
 **FAZER ✓** usar o tipo de parâmetro menos derivado que fornece a funcionalidade exigida pelo membro.  
  
 Por exemplo, suponha que você deseja criar um método que enumera uma coleção e imprime a cada item no console. Esse método um deve levar <xref:System.Collections.IEnumerable> como o parâmetro não <xref:System.Collections.ArrayList> ou <xref:System.Collections.IList>, por exemplo.  
  
 **X não** usar parâmetros reservados.  
  
 Se for necessário mais de entrada para um membro em alguma versão futura, pode ser adicionada uma sobrecarga de novo.  
  
 **X não** publicamente expor métodos que usam ponteiros, matrizes de ponteiros ou matrizes multidimensionais como parâmetros.  
  
 Ponteiros e matrizes multidimensionais são relativamente difícil de usar corretamente. Em quase todos os casos, APIs podem ser reprojetados para evitar deixar esses tipos como parâmetros.  
  
 **FAZER ✓** colocar todos os `out` parâmetros após todos o por valor e `ref` parâmetros (excluindo matrizes de parâmetros), mesmo se ele resulta em uma inconsistência no parâmetro ordenação entre sobrecargas (consulte [membro Sobrecarga](../../../docs/standard/design-guidelines/member-overloading.md)).  
  
 O `out` parâmetros podem ser vistos como valores de retorno extra e agrupá-los juntos torna mais fácil de entender a assinatura do método.  
  
 **FAZER ✓** seja consistente em nomes de parâmetros ao substituir membros ou implementar membros de interface.  
  
 Isso se comunica melhor a relação entre os métodos.  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a>Escolhendo entre Enum e parâmetros booleanos  
 **FAZER ✓** usar enums se um membro tivesse dois ou mais parâmetros booleanos.  
  
 **X não** usar valores booleanos, a menos que você tiver certeza absoluta nunca haverá a necessidade de mais de dois valores.  
  
 Enums dão espaço para futura inclusão dos valores, mas você deve estar ciente das implicações de adicionar valores para enums, que são descritos em [Enum Design](../../../docs/standard/design-guidelines/enum.md).  
  
 **✓ CONSIDERE** usando boolianos para parâmetros de construtor que são valores de dois estados realmente e são usados simplesmente para inicializar propriedades Boolianas.  
  
### <a name="validating-arguments"></a>Validar argumentos  
 **FAZER ✓** validar argumentos passados para membros públicos, protegidos ou implementados explicitamente. Lançar <xref:System.ArgumentException?displayProperty=nameWithType>, ou uma de suas subclasses, se a validação falhar.  
  
 Observe que a validação real não precisam necessariamente acontecer no membro público ou protegido em si. Isso pode acontecer em um nível inferior na rotina alguns privada ou interna. O ponto principal é que a área de superfície inteira que é exposta aos usuários finais verifica se os argumentos.  
  
 **FAZER ✓** gerar <xref:System.ArgumentNullException> se um argumento nulo é passado e o membro não oferece suporte a argumentos nulos.  
  
 **FAZER ✓** validar parâmetros de enum.  
  
 Não suponha enum argumentos serão no intervalo definido pela enumeração. O CLR permite converter qualquer valor inteiro em um valor de enumeração, mesmo se o valor não está definido na enum.  
  
 **X não** usar <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> para o intervalo de enum verifica.  
  
 **FAZER ✓** Lembre-se de que os argumentos mutáveis podem ter alterado depois que eles foram validados.  
  
 Se o membro for sensível à segurança, você é incentivado a fazer uma cópia e, em seguida, validar e processar o argumento.  
  
### <a name="parameter-passing"></a>Passagem de parâmetro  
 Da perspectiva de um designer de estrutura, há três grupos principais de parâmetros: parâmetros por valor `ref` parâmetros, e `out` parâmetros.  
  
 Quando um argumento é passado por meio de um parâmetro por valor, o membro recebe uma cópia do argumento real passado. Se o argumento for um tipo de valor, uma cópia do argumento é colocada na pilha. Se o argumento for um tipo de referência, uma cópia da referência é colocada na pilha. Idiomas mais populares de CLR, como c#, VB.NET e C++, padrão para passar parâmetros por valor.  
  
 Quando um argumento é passado por meio de um `ref` parâmetro, o membro recebe uma referência para o argumento passado. Se o argumento for um tipo de valor, uma referência para o argumento é colocada na pilha. Se o argumento for um tipo de referência, uma referência para a referência é colocada na pilha. `Ref`parâmetros podem ser usados para permitir que o membro modificar os argumentos passados pelo chamador.  
  
 `Out`parâmetros são semelhantes às `ref` parâmetros, com algumas pequenas diferenças. O parâmetro é considerado inicialmente não atribuídos e não pode ser lido no corpo do membro antes de ser atribuído um valor. Além disso, o parâmetro deve ser atribuído um valor antes de retorna o membro.  
  
 **X Evite** usando `out` ou `ref` parâmetros.  
  
 Usando `out` ou `ref` parâmetros requer experiência com ponteiros, compreender a diferença entre tipos de valor e tipos de referência e tratamento de métodos com vários valores de retorno. Além disso, a diferença entre `out` e `ref` parâmetros não é compreendido amplamente. Arquitetos de estrutura criando para o público em geral não devem esperar que os usuários mestre trabalhar com `out` ou `ref` parâmetros.  
  
 **X não** passar tipos de referência por referência.  
  
 Há algumas exceções limitadas para a regra, como um método que pode ser usada para trocar as referências.  
  
### <a name="members-with-variable-number-of-parameters"></a>Membros com um número variável de parâmetros  
 Membros que podem levar a um número variável de argumentos são expressos, fornecendo um parâmetro de matriz. Por exemplo, <xref:System.String> fornece o seguinte método:  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 Um usuário pode chamar o <xref:System.String.Format%2A?displayProperty=nameWithType> método, da seguinte maneira:  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 Adicionando a palavra-chave c# parâmetros para um parâmetro de matriz altera o parâmetro para um parâmetro de matriz de parâmetros chamados e fornece um atalho para a criação de uma matriz temporária.  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 Isso permite que o usuário chamar o método, passando os elementos da matriz diretamente na lista de argumentos.  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 Observe que a palavra-chave params pode ser adicionada somente para o último parâmetro na lista de parâmetros.  
  
 **✓ CONSIDERE** adicionando a palavra-chave params para parâmetros de matriz, se você espera que os usuários finais para transmitir matrizes com um pequeno número de elementos. Se for esperado que muitos elementos serão passados em comum cenários, os usuários provavelmente não passar esses elementos embutidos assim mesmo e portanto a palavra-chave params não é necessária.  
  
 **X Evite** usando matrizes de parâmetros se o chamador quase sempre deve ter a entrada já em uma matriz.  
  
 Por exemplo, membros com parâmetros da matriz de bytes quase nunca serão chamados passando bytes individuais. Por esse motivo, parâmetros de matriz de bytes no .NET Framework não usam a palavra-chave params.  
  
 **X não** usar matrizes de parâmetros, se a matriz é modificada pelo membro levando o parâmetro de matriz de parâmetros.  
  
 Devido ao fato de que muitos compiladores transformar os argumentos para o membro em uma matriz temporária no site de chamada, a matriz pode ser um objeto temporário e, portanto, qualquer modificação para a matriz serão perdidas.  
  
 **✓ CONSIDERE** usando a palavra-chave params em uma sobrecarga simple, mesmo se uma sobrecarga mais complexa não pode usá-lo.  
  
 Pergunte se os usuários seriam valor com a matriz de parâmetros em uma sobrecarga, mesmo se ele não estava em todas as sobrecargas.  
  
 **FAZER ✓** tente parâmetros de ordem para que seja possível usar a palavra-chave params.  
  
 **✓ CONSIDERE** fornecendo sobrecargas especiais e caminhos de código para chamadas com um pequeno número de argumentos nas APIs de desempenho extremamente sensíveis.  
  
 Isso torna possível para evitar a criação de objetos da matriz quando a API é chamada com um pequeno número de argumentos. Formam os nomes dos parâmetros considerando uma forma singular de parâmetro de matriz e adicionando um sufixo numérico.  
  
 Você deve fazer isso apenas se você for para casos especiais o caminho de código inteiro, não apenas criar uma matriz e chame o método mais geral.  
  
 **FAZER ✓** Lembre-se de que null pode ser passado como um argumento de matriz de parâmetros.  
  
 Você deve validar que a matriz não é nula antes do processamento.  
  
 **X não** usar o `varargs` métodos, também conhecidos como o botão de reticências.  
  
 Algumas linguagens CLR, como C++, dar suporte a uma convenção alternativa para a passagem de listas de parâmetros variáveis chamadas `varargs` métodos. A convenção não deve ser usada em estruturas, porque ele não é compatível com CLS.  
  
### <a name="pointer-parameters"></a>Parâmetros de ponteiro  
 Em geral, os ponteiros não devem aparecer na área de superfície pública de uma estrutura bem projetado de código gerenciado. Na maioria das vezes, os ponteiros devem ser encapsulados. No entanto, em alguns casos ponteiros são necessários por motivos de interoperabilidade, e usar ponteiros nesses casos é apropriado.  
  
 **FAZER ✓** fornecem uma alternativa para qualquer membro que usa um argumento de ponteiro, como ponteiros não são compatíveis com CLS.  
  
 **X Evite** fazendo caro argumento verificação de argumentos de ponteiro.  
  
 **FAZER ✓** convenções comuns relacionados ao ponteiro durante a criação de membros com ponteiros.  
  
 Por exemplo, não há nenhuma necessidade de passar o índice inicial, porque aritmética de ponteiro simple pode ser usada para obter o mesmo resultado.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de Design de membro](../../../docs/standard/design-guidelines/member.md)  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
