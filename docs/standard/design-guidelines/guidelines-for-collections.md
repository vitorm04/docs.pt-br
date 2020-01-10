---
title: Diretrizes para coleções
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
ms.openlocfilehash: 231d8b04c11f19c4440e184533e1eeaded72b70b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709316"
---
# <a name="guidelines-for-collections"></a>Diretrizes para coleções
Qualquer tipo projetado especificamente para manipular um grupo de objetos com alguma característica comum pode ser considerado uma coleção. É quase sempre apropriado para tais tipos implementarem <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>, portanto, nesta seção, apenas consideramos os tipos que implementam uma ou ambas as interfaces para serem coleções.  
  
 **X DO NOT** usar coleções sem rigidez de tipos em APIs públicas.  
  
 O tipo de todos os valores de retorno e parâmetros que representam itens de coleta deve ser o tipo de item exato, não qualquer um de seus tipos base (isso se aplica somente a membros públicos da coleção).  
  
 **X DO NOT** usar <xref:System.Collections.ArrayList> ou <xref:System.Collections.Generic.List%601> em APIs públicas.  
  
 Esses tipos são estruturas de dados projetadas para serem usadas na implementação interna, não em APIs públicas. a `List<T>` é otimizada para desempenho e potência no custo da limpeza das APIs e da flexibilidade. Por exemplo, se você retornar `List<T>`, ainda não será possível receber notificações quando o código do cliente modificar a coleção. Além disso, `List<T>` expõe vários membros, como <xref:System.Collections.Generic.List%601.BinarySearch%2A>, que não são úteis ou aplicáveis em muitos cenários. As duas seções a seguir descrevem tipos (abstrações) projetados especificamente para uso em APIs públicas.  
  
 **X DO NOT** usar `Hashtable` ou `Dictionary<TKey,TValue>` em APIs públicas.  
  
 Esses tipos são estruturas de dados projetadas para serem usadas na implementação interna. As APIs públicas devem usar <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`ou um tipo personalizado que implemente uma ou ambas as interfaces.  
  
 **X DO NOT** usar <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>, ou qualquer outro tipo que implementa uma dessas interfaces, exceto como o tipo de retorno de um `GetEnumerator` método.  
  
 Tipos que retornam enumeradores de métodos diferentes de `GetEnumerator` não podem ser usados com a instrução `foreach`.  
  
 **X DO NOT** implementar `IEnumerator<T>` e `IEnumerable<T>` do mesmo tipo. O mesmo se aplica às interfaces não genéricas `IEnumerator` e `IEnumerable`.  
  
## <a name="collection-parameters"></a>Parâmetros de coleta  
 **✓ DO** usar o possível tipo especializado de menos como um tipo de parâmetro. A maioria dos membros que tomam coleções como parâmetros usa a interface `IEnumerable<T>`.  
  
 **X AVOID** usando <xref:System.Collections.Generic.ICollection%601> ou <xref:System.Collections.ICollection> como um parâmetro apenas para acessar o `Count` propriedade.  
  
 Em vez disso, considere usar `IEnumerable<T>` ou `IEnumerable` e verificar dinamicamente se o objeto implementa `ICollection<T>` ou `ICollection`.  
  
## <a name="collection-properties-and-return-values"></a>Propriedades de coleção e valores de retorno  
 **X DO NOT** fornecem propriedades de coleção configurável.  
  
 Os usuários podem substituir o conteúdo da coleção limpando a coleção primeiro e, em seguida, adicionando o novo conteúdo. Se substituir a coleção inteira for um cenário comum, considere fornecer o método `AddRange` na coleção.  
  
 **✓ DO** usar `Collection<T>` ou uma subclasse de `Collection<T>` para propriedades ou retornam valores que representam coleções de leitura/gravação.  
  
 Se `Collection<T>` não atender a algum requisito (por exemplo, a coleção não deve implementar <xref:System.Collections.IList>), use uma coleção personalizada implementando `IEnumerable<T>`, `ICollection<T>`ou <xref:System.Collections.Generic.IList%601>.  
  
 **✓ DO** usar <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, uma subclasse de `ReadOnlyCollection<T>`, ou em casos raros `IEnumerable<T>` para propriedades ou retorno de valores que representam coleções somente leitura.  
  
 Em geral, prefira `ReadOnlyCollection<T>`. Se ele não atender a algum requisito (por exemplo, a coleção não deve implementar `IList`), use uma coleção personalizada implementando `IEnumerable<T>`, `ICollection<T>`ou `IList<T>`. Se você implementar uma coleção personalizada somente leitura, implemente `ICollection<T>.IsReadOnly` para retornar `true`.  
  
 Nos casos em que você tem certeza de que o único cenário para o qual você deseja dar suporte é iteração somente de encaminhamento, você pode simplesmente usar `IEnumerable<T>`.  
  
 **✓ CONSIDER** usando as subclasses de coleções genéricas de base em vez de usar as coleções diretamente.  
  
 Isso permite um nome melhor e para adicionar membros auxiliares que não estão presentes nos tipos de coleção base. Isso é especialmente aplicável a APIs de alto nível.  
  
 **✓ CONSIDER** retornando uma subclasse de `Collection<T>` ou `ReadOnlyCollection<T>` de propriedades e métodos muito mais usados.  
  
 Isso possibilitará que você adicione métodos auxiliares ou altere a implementação da coleção no futuro.  
  
 **✓ CONSIDER** usando uma coleção com chave se os itens armazenados na coleção têm chaves exclusivas (nomes, IDs, etc.). Coleções com chave são coleções que podem ser indexadas por um inteiro e uma chave e geralmente são implementadas herdando de `KeyedCollection<TKey,TItem>`.  
  
 Coleções com chave geralmente têm grandes volumes de memória e não devem ser usadas se a sobrecarga de memória supera os benefícios de ter as chaves.  
  
 **X DO NOT** retornar valores nulos de propriedades de coleção ou de métodos de retorno de coleções. Em vez disso, retorne uma coleção vazia ou uma matriz vazia.  
  
 A regra geral é que as coleções e as matrizes NULL e Empty (0 item) devem ser tratadas da mesma.  
  
### <a name="snapshots-versus-live-collections"></a>Instantâneos versus coleções ao vivo  
 As coleções que representam um estado em algum momento são chamadas de coleções de instantâneos. Por exemplo, uma coleção que contém linhas retornadas de uma consulta de banco de dados seria um instantâneo. As coleções que sempre representam o estado atual são chamadas de coleções dinâmicas. Por exemplo, uma coleção de itens de `ComboBox` é uma coleção dinâmica.  
  
 **X DO NOT** retornam coleções de instantâneo de propriedades. As propriedades devem retornar coleções dinâmicas.  
  
 Os getters de propriedade devem ser operações muito leves. Retornar um instantâneo requer a criação de uma cópia de uma coleção interna em uma operação O (n).  
  
 **✓ DO** usar uma coleção de instantâneo ou de um live `IEnumerable<T>` (ou seu subtipo) para representar as coleções são voláteis (ou seja, que pode alterar sem modificar explicitamente a coleção).  
  
 Em geral, todas as coleções que representam um recurso compartilhado (por exemplo, arquivos em um diretório) são voláteis. Essas coleções são muito difíceis ou impossíveis de implementar como coleções dinâmicas, a menos que a implementação seja simplesmente um enumerador somente de encaminhamento.  
  
## <a name="choosing-between-arrays-and-collections"></a>Escolhendo entre matrizes e coleções  
 **✓ DO** prefira a matrizes de coleções.  
  
 As coleções fornecem mais controle sobre o conteúdo, podem evoluir ao longo do tempo e são mais utilizáveis. Além disso, o uso de matrizes para cenários somente leitura é desencorajado porque o custo da clonagem da matriz é proibitivo. Estudos de usabilidade mostraram que alguns desenvolvedores se sentem mais confortáveis usando APIs baseadas em coleção.  
  
 No entanto, se você estiver desenvolvendo APIs de nível baixo, talvez seja melhor usar matrizes para cenários de leitura/gravação. As matrizes têm uma superfície de memória menor, o que ajuda a reduzir o conjunto de trabalho, e o acesso a elementos em uma matriz é mais rápido porque é otimizado pelo tempo de execução.  
  
 **✓ CONSIDER** usando matrizes nas APIs de baixo nível para minimizar o consumo de memória e maximizar o desempenho.  
  
 **✓ DO** usar matrizes de bytes em vez de coleções de bytes.  
  
 **X DO NOT** usar matrizes de propriedades, se a propriedade teria que retornar uma nova matriz (por exemplo, uma cópia de uma matriz interna) sempre que a propriedade getter é chamado.  
  
## <a name="implementing-custom-collections"></a>Implementando coleções personalizadas  
 **✓ CONSIDER** herdando `Collection<T>`, `ReadOnlyCollection<T>`, ou `KeyedCollection<TKey,TItem>` durante a criação de novas coleções.  
  
 **✓ DO** implementar `IEnumerable<T>` durante a criação de novas coleções. Considere implementar `ICollection<T>` ou até mesmo `IList<T>` onde faz sentido.  
  
 Ao implementar essa coleção personalizada, siga o padrão de API estabelecido por `Collection<T>` e `ReadOnlyCollection<T>` o mais próximo possível. Ou seja, implemente os mesmos membros explicitamente, nomeie os parâmetros como essas duas coleções, e assim por diante.  
  
 **✓ CONSIDER** implementando interfaces de coleção não genérica (`IList` e `ICollection`) se a coleção será geralmente passada para APIs colocar essas interfaces como entrada.  
  
 **X AVOID** implementando interfaces de coleção em tipos com APIs complexas não relacionados ao conceito de uma coleção.  
  
 **X DO NOT** herdam coleções não genéricas de base como `CollectionBase`. Use `Collection<T>`, `ReadOnlyCollection<T>`e `KeyedCollection<TKey,TItem>` em vez disso.  
  
### <a name="naming-custom-collections"></a>Nomeando coleções personalizadas  
 Coleções (tipos que implementam `IEnumerable`) são criadas principalmente por dois motivos: (1) para criar uma nova estrutura de dados com operações específicas da estrutura e, muitas vezes, características de desempenho diferentes das estruturas de dados existentes (por exemplo, <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>) e (2) para criar uma coleção especializada para manter um conjunto específico de itens (por exemplo, <xref:System.Collections.Specialized.StringCollection>). As estruturas de dados são geralmente usadas na implementação interna de aplicativos e bibliotecas. Coleções especializadas são principalmente expostas em APIs (como tipos de propriedade e de parâmetro).  
  
 **✓ DO** utilize o sufixo "Dicionário" em nomes de abstrações implementando `IDictionary` ou `IDictionary<TKey,TValue>`.  
  
 **✓ DO** utilize o sufixo "Coleção" em nomes de tipos que implementam `IEnumerable` (ou qualquer um de seus descendentes) e que representa uma lista de itens.  
  
 **✓ DO** usar o nome de estrutura de dados apropriados para estruturas de dados personalizadas.  
  
 **X AVOID** usando qualquer sufixo implicando implementação específica, como "LinkedList" ou "Tabela de hash", em nomes de abstrações de coleção.  
  
 **✓ CONSIDER** prefixando nomes de coleção com o nome do tipo de item. Por exemplo, uma coleção que armazena itens do tipo `Address` (implementando `IEnumerable<Address>`) deve ser nomeada `AddressCollection`. Se o tipo de item for uma interface, o prefixo "I" do tipo de item poderá ser omitido. Assim, uma coleção de itens de <xref:System.IDisposable> pode ser chamada `DisposableCollection`.  
  
 **✓ CONSIDER** usando o prefixo "ReadOnly" em nomes de coleções somente leitura se uma coleção gravável correspondente pode ser adicionada ou já existe no framework.  
  
 Por exemplo, uma coleção de cadeias de caracteres somente leitura deve ser chamada `ReadOnlyStringCollection`.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Veja também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de uso](../../../docs/standard/design-guidelines/usage-guidelines.md)
