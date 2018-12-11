---
title: Diretrizes para coleções
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
author: KrzysztofCwalina
ms.openlocfilehash: 12f086ac92b449e074b9d39a563a20a3ebf2ff26
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145576"
---
# <a name="guidelines-for-collections"></a>Diretrizes para coleções
Qualquer tipo projetado especificamente para manipular um grupo de objetos que têm algumas características comuns pode ser considerado uma coleção. Quase sempre é apropriado para esses tipos implementar <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>, portanto, nesta seção consideramos apenas tipos que implementam uma ou ambas dessas interfaces para ser coleções.  
  
 **X DO NOT** usar coleções sem rigidez de tipos em APIs públicas.  
  
 O tipo de todos os valores de retorno e parâmetros que representam itens de coleta deve ser do tipo de item exato, não qualquer um dos seus tipos base (isso se aplica apenas a membros públicos da coleção).  
  
 **X DO NOT** usar <xref:System.Collections.ArrayList> ou <xref:System.Collections.Generic.List%601> em APIs públicas.  
  
 Esses tipos são estruturas de dados projetadas para ser usado na implementação interna, não em APIs públicas. `List<T>` é otimizado para desempenho e energia às custas de cleanness das APIs e flexibilidade. Por exemplo, se você retornar `List<T>`, você não será capaz de receber notificações quando o código do cliente modifica a coleção. Além disso, `List<T>` expõe o número de membros, como <xref:System.Collections.Generic.List%601.BinarySearch%2A>, que não são úteis ou aplicável em muitos cenários. As seções a seguir descrevem os tipos (abstrações) desenvolvidos especificamente para uso em APIs públicas.  
  
 **X DO NOT** usar `Hashtable` ou `Dictionary<TKey,TValue>` em APIs públicas.  
  
 Esses tipos são estruturas de dados projetadas para ser usado na implementação interna. Use as APIs públicas <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`, ou um tipo personalizado implementando uma ou ambas as interfaces.  
  
 **X DO NOT** usar <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>, ou qualquer outro tipo que implementa uma dessas interfaces, exceto como o tipo de retorno de um `GetEnumerator` método.  
  
 Tipos de retorno diferente de enumeradores métodos `GetEnumerator` não pode ser usado com o `foreach` instrução.  
  
 **X DO NOT** implementar `IEnumerator<T>` e `IEnumerable<T>` do mesmo tipo. O mesmo se aplica às interfaces não genéricas `IEnumerator` e `IEnumerable`.  
  
## <a name="collection-parameters"></a>Parâmetros de coleta  
 **✓ DO** usar o possível tipo especializado de menos como um tipo de parâmetro. A maioria dos membros levando coleções como usam parâmetros de `IEnumerable<T>` interface.  
  
 **X AVOID** usando <xref:System.Collections.Generic.ICollection%601> ou <xref:System.Collections.ICollection> como um parâmetro apenas para acessar o `Count` propriedade.  
  
 Em vez disso, considere o uso de `IEnumerable<T>` ou `IEnumerable` e dinamicamente, verificando se o objeto implementa `ICollection<T>` ou `ICollection`.  
  
## <a name="collection-properties-and-return-values"></a>Coleção de propriedades e valores de retorno  
 **X DO NOT** fornecem propriedades de coleção configurável.  
  
 Os usuários podem substituir o conteúdo da coleção de limpar a coleção primeiro e, em seguida, adicionando o novo conteúdo. Se substituir toda a coleção é um cenário comum, recomenda-se de fornecer o `AddRange` método na coleção.  
  
 **✓ DO** usar `Collection<T>` ou uma subclasse de `Collection<T>` para propriedades ou retornam valores que representam coleções de leitura/gravação.  
  
 Se `Collection<T>` não atender a alguns requisitos (por exemplo, a coleção não deve implementar <xref:System.Collections.IList>), usar uma coleção personalizada implementando `IEnumerable<T>`, `ICollection<T>`, ou <xref:System.Collections.Generic.IList%601>.  
  
 **✓ DO** usar <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, uma subclasse de `ReadOnlyCollection<T>`, ou em casos raros `IEnumerable<T>` para propriedades ou retorno de valores que representam coleções somente leitura.  
  
 Em geral, prefira `ReadOnlyCollection<T>`. Se ele não atender a algum requisito (por exemplo, a coleção não deve implementar `IList`), usar uma coleção personalizada implementando `IEnumerable<T>`, `ICollection<T>`, ou `IList<T>`. Se você implementar uma coleção somente leitura personalizada, implemente `ICollection<T>.IsReadOnly` para retornar `true`.  
  
 Em casos onde você está-se de que o único cenário em que você nunca deseja dar suporte a iteração de somente avanço, você pode simplesmente usar `IEnumerable<T>`.  
  
 **✓ CONSIDER** usando as subclasses de coleções genéricas de base em vez de usar as coleções diretamente.  
  
 Isso permite que um nome melhor e para a adição de membros de auxiliar que não estão presentes nos tipos de coleção base. Isso é especialmente aplicável para APIs de alto nível.  
  
 **✓ CONSIDER** retornando uma subclasse de `Collection<T>` ou `ReadOnlyCollection<T>` de propriedades e métodos muito mais usados.  
  
 Isso tornará possível para que você possa adicionar métodos auxiliares ou alterar a implementação da coleção no futuro.  
  
 **✓ CONSIDER** usando uma coleção com chave se os itens armazenados na coleção têm chaves exclusivas (nomes, IDs, etc.). Coleções de chave são coleções que podem ser indexadas por um número inteiro e uma chave e geralmente são implementadas herdando de `KeyedCollection<TKey,TItem>`.  
  
 Coleções de chave geralmente tem capacidades maiores de memória e não devem ser usadas se a sobrecarga de memória supera os benefícios de ter as chaves.  
  
 **X DO NOT** retornar valores nulos de propriedades de coleção ou de métodos de retorno de coleções. Em vez disso, retorne uma coleção vazia ou uma matriz vazia.  
  
 A regra geral é que as coleções (item 0) de null e vazias ou matrizes devem ser tratados da mesma.  
  
### <a name="snapshots-versus-live-collections"></a>Instantâneos Versus coleções ao vivo  
 Coleções de instantâneo são chamadas de coleções que representa um estado em algum ponto no tempo. Por exemplo, uma coleção que contém linhas retornadas de uma consulta de banco de dados seria um instantâneo. Coleções em tempo real são chamadas de coleções que sempre representam o estado atual. Por exemplo, uma coleção de `ComboBox` itens é uma coleção em tempo real.  
  
 **X DO NOT** retornam coleções de instantâneo de propriedades. As propriedades devem retornar coleções em tempo real.  
  
 Getters de propriedade devem ser operações muito leves. Retornar um instantâneo requer a criação de uma cópia de uma coleção interna em uma operação de (n).  
  
 **✓ DO** usar uma coleção de instantâneo ou de um live `IEnumerable<T>` (ou seu subtipo) para representar as coleções são voláteis (ou seja, que pode alterar sem modificar explicitamente a coleção).  
  
 Em geral, todas as coleções que representa um recurso compartilhado (por exemplo, arquivos em um diretório) são voláteis. Essas coleções são muito difíceis ou impossíveis de implementar como coleções em tempo real, a menos que a implementação é simplesmente um enumerador de somente avanço.  
  
## <a name="choosing-between-arrays-and-collections"></a>Escolhendo entre coleções e matrizes  
 **✓ DO** prefira a matrizes de coleções.  
  
 Coleções fornecem mais controle sobre o conteúdo, podem evoluir ao longo do tempo e são mais utilizáveis. Além disso, usar matrizes para cenários somente leitura não é recomendado porque o custo de clonagem da matriz é proibitivo. Estudos de usabilidade mostraram que alguns desenvolvedores se sentir mais confortáveis usando APIs baseadas em coleção.  
  
 No entanto, se você estiver desenvolvendo APIs de baixo nível, talvez seja melhor usar matrizes para cenários de leitura / gravação. As matrizes têm um menor volume de memória, que ajuda a reduzir o conjunto de trabalho, e o acesso a elementos em uma matriz é mais rápido porque é otimizado pelo tempo de execução.  
  
 **✓ CONSIDER** usando matrizes nas APIs de baixo nível para minimizar o consumo de memória e maximizar o desempenho.  
  
 **✓ DO** usar matrizes de bytes em vez de coleções de bytes.  
  
 **X DO NOT** usar matrizes de propriedades, se a propriedade teria que retornar uma nova matriz (por exemplo, uma cópia de uma matriz interna) sempre que a propriedade getter é chamado.  
  
## <a name="implementing-custom-collections"></a>Implementando coleções personalizadas  
 **✓ CONSIDER** herdando `Collection<T>`, `ReadOnlyCollection<T>`, ou `KeyedCollection<TKey,TItem>` durante a criação de novas coleções.  
  
 **✓ DO** implementar `IEnumerable<T>` durante a criação de novas coleções. Considere a implementação `ICollection<T>` ou até mesmo `IList<T>` onde faça sentido.  
  
 Ao implementar tal coleção personalizada, seguem o padrão de API estabelecido pela `Collection<T>` e `ReadOnlyCollection<T>` mais próximo possível. Ou seja, implementar os mesmos membros explicitamente, nomear os parâmetros, como essas duas coleções de nome-los e assim por diante.  
  
 **✓ CONSIDER** implementando interfaces de coleção não genérica (`IList` e `ICollection`) se a coleção será geralmente passada para APIs colocar essas interfaces como entrada.  
  
 **X AVOID** implementando interfaces de coleção em tipos com APIs complexas não relacionados ao conceito de uma coleção.  
  
 **X DO NOT** herdam coleções não genéricas de base como `CollectionBase`. Use `Collection<T>`, `ReadOnlyCollection<T>`, e `KeyedCollection<TKey,TItem>` em vez disso.  
  
### <a name="naming-custom-collections"></a>Coleções personalizadas de nomenclatura  
 Coleções (tipos que implementam `IEnumerable`) são criados basicamente por dois motivos: (1) para criar uma nova estrutura de dados com operações específicas de estrutura e muitas vezes diferentes características de desempenho que estruturas de dados existentes (por exemplo, <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>) e (2) para criar uma coleção especializada para mantendo um conjunto específico de itens (por exemplo, <xref:System.Collections.Specialized.StringCollection>). Estruturas de dados geralmente são usadas na implementação interna de aplicativos e bibliotecas. Coleções especializadas principalmente devem ser expostos nas APIs (como tipos de propriedade e de parâmetro).  
  
 **✓ DO** utilize o sufixo "Dicionário" em nomes de abstrações implementando `IDictionary` ou `IDictionary<TKey,TValue>`.  
  
 **✓ DO** utilize o sufixo "Coleção" em nomes de tipos que implementam `IEnumerable` (ou qualquer um de seus descendentes) e que representa uma lista de itens.  
  
 **✓ DO** usar o nome de estrutura de dados apropriados para estruturas de dados personalizadas.  
  
 **X AVOID** usando qualquer sufixo implicando implementação específica, como "LinkedList" ou "Tabela de hash", em nomes de abstrações de coleção.  
  
 **✓ CONSIDER** prefixando nomes de coleção com o nome do tipo de item. Por exemplo, uma coleção de itens do tipo de armazenamento `Address` (implementando `IEnumerable<Address>`) deve ser nomeado `AddressCollection`. Se o tipo de item é uma interface, o "I" prefixo de tipo do item pode ser omitido. Portanto, uma coleção de <xref:System.IDisposable> itens podem ser chamados `DisposableCollection`.  
  
 **✓ CONSIDER** usando o prefixo "ReadOnly" em nomes de coleções somente leitura se uma coleção gravável correspondente pode ser adicionada ou já existe no framework.  
  
 Por exemplo, uma coleção somente leitura de cadeias de caracteres deve ser chamada `ReadOnlyStringCollection`.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
- [Diretrizes de uso](../../../docs/standard/design-guidelines/usage-guidelines.md)
