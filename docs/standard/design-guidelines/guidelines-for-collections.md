---
title: "Diretrizes para coleções"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 09a2a075e21de6968989575385db07ab39eb627f
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2018
---
# <a name="guidelines-for-collections"></a>Diretrizes para coleções
Qualquer tipo projetado especificamente para manipular um grupo de objetos que têm algumas características comuns pode ser considerado uma coleção. Quase sempre é apropriado para esses tipos implementar <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>, portanto, nesta seção só consideramos tipos que implementam uma ou ambas as interfaces para coleções de ser.  
  
 **X não** usar coleções sem rigidez de tipos em APIs públicas.  
  
 O tipo de todos os valores de retorno e parâmetros que representa a coleção de itens deve ser o tipo de item exato, não os seus tipos base (isso se aplica apenas a membros públicos da coleção).  
  
 **X não** usar <xref:System.Collections.ArrayList> ou <xref:System.Collections.Generic.List%601> em APIs públicas.  
  
 Esses tipos são projetadas para serem usados na implementação interna, não em APIs públicas de estruturas de dados. `List<T>` é otimizado para desempenho e a potência à custa cleanness das APIs do e flexibilidade. Por exemplo, se você retornar `List<T>`, você não será capaz de receber notificações quando o código de cliente modificar a coleção. Além disso, `List<T>` expõe a muitos membros, como <xref:System.Collections.Generic.List%601.BinarySearch%2A>, que não são úteis ou aplicável em muitos cenários. As seções a seguir descrevem tipos (abstrações) projetados especificamente para ser usado em APIs públicas.  
  
 **X não** usar `Hashtable` ou `Dictionary<TKey,TValue>` em APIs públicas.  
  
 Esses tipos são projetadas para serem usados na implementação interna de estruturas de dados. Use APIs públicas <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`, ou um tipo personalizado implementando uma ou ambas as interfaces.  
  
 **X não** usar <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>, ou qualquer outro tipo que implementa uma dessas interfaces, exceto como o tipo de retorno de um `GetEnumerator` método.  
  
 Tipos retornando enumeradores de métodos diferentes de `GetEnumerator` não pode ser usado com o `foreach` instrução.  
  
 **X não** implementar `IEnumerator<T>` e `IEnumerable<T>` do mesmo tipo. O mesmo se aplica às interfaces genéricas `IEnumerator` e `IEnumerable`.  
  
## <a name="collection-parameters"></a>Coleção de parâmetros  
 **FAZER ✓** usar o possível tipo especializado de menos como um tipo de parâmetro. A maioria dos membros levando coleções como usam parâmetros de `IEnumerable<T>` interface.  
  
 **X Evite** usando <xref:System.Collections.Generic.ICollection%601> ou <xref:System.Collections.ICollection> como um parâmetro apenas para acessar o `Count` propriedade.  
  
 Em vez disso, considere o uso de `IEnumerable<T>` ou `IEnumerable` e dinamicamente, verificando se o objeto implementa `ICollection<T>` ou `ICollection`.  
  
## <a name="collection-properties-and-return-values"></a>Coleção de propriedades e valores de retorno  
 **X não** fornecem propriedades de coleção configurável.  
  
 Os usuários podem substituir o conteúdo da coleção de limpar a coleção pela primeira vez e, em seguida, adicionando o novo conteúdo. Se substituir toda a coleção é um cenário comum, recomenda-se de fornecer o `AddRange` método na coleção.  
  
 **FAZER ✓** usar `Collection<T>` ou uma subclasse de `Collection<T>` para propriedades ou retornam valores que representam coleções de leitura/gravação.  
  
 Se `Collection<T>` não atender a algum requisito (por exemplo, a coleção deve implementar não <xref:System.Collections.IList>), use uma coleção personalizada implementando `IEnumerable<T>`, `ICollection<T>`, ou <xref:System.Collections.Generic.IList%601>.  
  
 **FAZER ✓** usar <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, uma subclasse de `ReadOnlyCollection<T>`, ou em casos raros `IEnumerable<T>` para propriedades ou retorno de valores que representam coleções somente leitura.  
  
 Em geral, prefira `ReadOnlyCollection<T>`. Se ele não atender a algum requisito (por exemplo, a coleção deve implementar não `IList`), use uma coleção personalizada implementando `IEnumerable<T>`, `ICollection<T>`, ou `IList<T>`. Se você implementar um conjunto personalizado de somente leitura, implementar `ICollection<T>.IsReadOnly` para retornar `true`.  
  
 Em casos onde você tiver certeza de que o único cenário em que você nunca deseja dar suporte a iteração de somente avanço, você pode simplesmente usar `IEnumerable<T>`.  
  
 **✓ CONSIDERE** usando as subclasses de coleções genéricas de base em vez de usar as coleções diretamente.  
  
 Isso permite que um nome melhor e para adicionar membros de auxiliar que não estão presentes nos tipos de coleção de base. Isso é especialmente aplicável às APIs de alto nível.  
  
 **✓ CONSIDERE** retornando uma subclasse de `Collection<T>` ou `ReadOnlyCollection<T>` de propriedades e métodos muito mais usados.  
  
 Isso tornará possível para adicionar métodos auxiliares ou altere a implementação de coleção no futuro.  
  
 **✓ CONSIDERE** usando uma coleção com chave se os itens armazenados na coleção têm chaves exclusivas (nomes, IDs, etc.). Coleções de chave são coleções que podem ser indexadas por um número inteiro e uma chave e são normalmente implementadas herdando de `KeyedCollection<TKey,TItem>`.  
  
 Coleções de chave normalmente têm o maior benefício de memória e não devem ser usadas se a sobrecarga de memória supera os benefícios de ter as chaves.  
  
 **X não** retornar valores nulos de propriedades de coleção ou de métodos de retorno de coleções. Retorna uma coleção vazia ou uma matriz vazia em vez disso.  
  
 A regra geral é que as coleções de (item 0) nulas e vazias ou matrizes devem ser tratado da mesma.  
  
### <a name="snapshots-versus-live-collections"></a>Instantâneos Versus coleções ao vivo  
 Coleções de instantâneo são chamadas de coleções que representa um estado em um determinado ponto no tempo. Por exemplo, uma coleção que contém linhas retornadas de uma consulta de banco de dados seria um instantâneo. Coleções que sempre representam o estado atual são chamadas de coleções ao vivo. Por exemplo, uma coleção de `ComboBox` itens é uma coleção dinâmica.  
  
 **X não** retornam coleções de instantâneo de propriedades. Propriedades devem retornar coleções ao vivo.  
  
 Getters de propriedade devem ser operações muito simples. Retornar um instantâneo requer a criação de uma cópia de uma coleção interna em uma operação (n).  
  
 **FAZER ✓** usar uma coleção de instantâneo ou de um live `IEnumerable<T>` (ou seu subtipo) para representar as coleções são voláteis (ou seja, que pode alterar sem modificar explicitamente a coleção).  
  
 Em geral, todas as coleções que representa um recurso compartilhado (por exemplo, arquivos em um diretório) são voláteis. Essas coleções são muito difíceis ou impossíveis de implementar como coleções ao vivo, a menos que a implementação é simplesmente um enumerador de somente avanço.  
  
## <a name="choosing-between-arrays-and-collections"></a>Escolhendo entre matrizes e coleções  
 **FAZER ✓** prefira a matrizes de coleções.  
  
 Coleções fornecem mais controle sobre o conteúdo, podem evoluir ao longo do tempo e são mais úteis. Além disso, usando matrizes para cenários de somente leitura não é recomendado porque o custo de clonagem da matriz é proibitivo. Estudos de usabilidade mostram que alguns desenvolvedores achar mais fácil usar APIs baseadas em coleção.  
  
 No entanto, se você estiver desenvolvendo APIs de baixo nível, talvez seja melhor usar matrizes para cenários de leitura / gravação. As matrizes têm um menor volume de memória, o que ajuda a reduzir o conjunto de trabalho, e o acesso a elementos em uma matriz é mais rápido porque ele é otimizado pelo tempo de execução.  
  
 **✓ CONSIDERE** usando matrizes nas APIs de baixo nível para minimizar o consumo de memória e maximizar o desempenho.  
  
 **FAZER ✓** usar matrizes de bytes em vez de coleções de bytes.  
  
 **X não** usar matrizes de propriedades, se a propriedade teria que retornar uma nova matriz (por exemplo, uma cópia de uma matriz interna) sempre que a propriedade getter é chamado.  
  
## <a name="implementing-custom-collections"></a>Implementando coleções personalizadas  
 **✓ CONSIDERE** herdando `Collection<T>`, `ReadOnlyCollection<T>`, ou `KeyedCollection<TKey,TItem>` durante a criação de novas coleções.  
  
 **FAZER ✓** implementar `IEnumerable<T>` durante a criação de novas coleções. Considere implementar `ICollection<T>` ou até mesmo `IList<T>` onde faz sentido.  
  
 Ao implementar essa coleção personalizada, seguem o padrão de API estabelecido por `Collection<T>` e `ReadOnlyCollection<T>` mais próximo possível. Isto é, implemente os mesmos membros explicitamente, nomear os parâmetros como essas duas coleções de nome-los e assim por diante.  
  
 **✓ CONSIDERE** implementando interfaces de coleção não genérica (`IList` e `ICollection`) se a coleção será geralmente passada para APIs colocar essas interfaces como entrada.  
  
 **X Evite** implementando interfaces de coleção em tipos com APIs complexas não relacionados ao conceito de uma coleção.  
  
 **X não** herdam coleções não genéricas de base como `CollectionBase`. Use `Collection<T>`, `ReadOnlyCollection<T>`, e `KeyedCollection<TKey,TItem>` em vez disso.  
  
### <a name="naming-custom-collections"></a>Coleções personalizadas de nomenclatura  
 Coleções (tipos que implementam `IEnumerable`) são criados principalmente por duas razões: (1) para criar uma nova estrutura de dados com operações específicas de estrutura e geralmente diferentes características de desempenho de estruturas de dados existente (por exemplo, <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>) e (2) para criar uma coleção especializada para manter um conjunto específico de itens (por exemplo, <xref:System.Collections.Specialized.StringCollection>). Estruturas de dados são geralmente usadas na implementação interna de aplicativos e bibliotecas. Coleções especializadas principalmente devem ser expostos nas APIs (como tipos de parâmetro e de propriedade).  
  
 **FAZER ✓** utilize o sufixo "Dicionário" em nomes de abstrações implementando `IDictionary` ou `IDictionary<TKey,TValue>`.  
  
 **FAZER ✓** utilize o sufixo "Coleção" em nomes de tipos que implementam `IEnumerable` (ou qualquer um de seus descendentes) e que representa uma lista de itens.  
  
 **FAZER ✓** usar o nome de estrutura de dados apropriados para estruturas de dados personalizadas.  
  
 **X Evite** usando qualquer sufixo implicando implementação específica, como "LinkedList" ou "Tabela de hash", em nomes de abstrações de coleção.  
  
 **✓ CONSIDERE** prefixando nomes de coleção com o nome do tipo de item. Por exemplo, uma coleção de itens do tipo de armazenamento `Address` (implementando `IEnumerable<Address>`) deve ser nomeado `AddressCollection`. Se o tipo de item é uma interface, "I" prefixo do item de tipo pode ser omitido. Portanto, uma coleção de <xref:System.IDisposable> itens podem ser chamados `DisposableCollection`.  
  
 **✓ CONSIDERE** usando o prefixo "ReadOnly" em nomes de coleções somente leitura se uma coleção gravável correspondente pode ser adicionada ou já existe no framework.  
  
 Por exemplo, uma coleção somente leitura de cadeias de caracteres deve ser chamada `ReadOnlyStringCollection`.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Diretrizes de uso](../../../docs/standard/design-guidelines/usage-guidelines.md)
