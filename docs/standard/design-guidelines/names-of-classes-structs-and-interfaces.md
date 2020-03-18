---
title: Nomes de classes, structs e interfaces
ms.date: 10/22/2008
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
ms.openlocfilehash: 2c528348c0e84037a80df9797c56f03b51c73adc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400592"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Nomes de classes, structs e interfaces
As diretrizes de nomeação que seguem aplicam-se à nomeação geral do tipo.

 ✔️ DO nome classes e structs com nomes de nomes ou frases de nomes, usando PascalCasing.

 Isso distingue nomes de tipos de métodos, que são nomeados com frases verbais.

 ✔️ do nome DO interfaces com frases adjetivas, ou ocasionalmente com nomes de nomes ou nomes de nomes.

 Substantivos e frases substantivas devem ser usados raramente e podem indicar que o tipo deve ser uma classe abstrata, e não uma interface.

 ❌NÃO dê aos nomes de classe um prefixo (por exemplo, "C").

 ✔️ CONSIDEREm acabar com o nome de classes derivadas com o nome da classe base.

 Isso é muito legível e explica a relação claramente. Alguns exemplos disso em `ArgumentOutOfRangeException`código são: , `Exception`que `SerializableAttribute`é uma espécie `Attribute`de , e , que é uma espécie de . No entanto, é importante usar o juízo razoável na aplicação desta diretriz; por exemplo, `Button` a classe `Control` é um `Control` tipo de evento, embora não apareça em seu nome.

 ✔️ NOMES de interface de prefixo DO com a letra I, para indicar que o tipo é uma interface.

 Por exemplo, `IComponent` (unsante `ICustomAttributeProvider` descritivo), `IPersistable` (frase de nome de unisstan) e (adjetivo) são nomes de interface apropriados. Como acontece com outros nomes de tipos, evite abreviaturas.

 ✔️ DO certifique-se de que os nomes diferem apenas pelo prefixo "I" no nome da interface quando você estiver definindo um par de interface de classe onde a classe é uma implementação padrão da interface.

## <a name="names-of-generic-type-parameters"></a>Nomes de parâmetros de tipo genéricos
 Os genéricos foram adicionados ao .NET Framework 2.0. O recurso introduziu um novo tipo de identificador chamado *parâmetro de tipo*.

 ✔️ do nome do parâmetros genéricos de tipo com nomes descritivos, a menos que um nome de uma única letra seja completamente auto-explicativo e um nome descritivo não agregaria valor.

 ✔️ CONSIDEREM usar `T` como nome de parâmetro de tipo para tipos com um parâmetro de tipo de letra única.

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 ✔️ nomes de parâmetro de tipo `T`descritivo do prefixo DO com .

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 ✔️ CONSIDEREM indicar restrições colocadas em um parâmetro de tipo em nome do parâmetro.

 Por exemplo, um parâmetro `ISession` constrangido pode ser chamado `TSession`de .

## <a name="names-of-common-types"></a>Nomes de Tipos Comuns
 ✔️ DO siga as diretrizes descritas na tabela a seguir ao nomear tipos derivados ou implementar certos tipos de framework .NET.

|Tipo de base|Diretriz do tipo derivado/implementante|
|---------------|------------------------------------------|
|`System.Attribute`|✔️ DO adicionam o sufixo "Atributo" a nomes de classes de atributos personalizados.|
|`System.Delegate`|✔️ DO adicione o sufixo "EventHandler" aos nomes dos delegados que são usados em eventos.<br /><br /> ✔️ DO adicione o sufixo "Callback" aos nomes de delegados que não sejam os usados como manipuladores de eventos.<br /><br /> ❌NÃO adicione o sufixo "Delegado" a um delegado.|
|`System.EventArgs`|✔️ DO adicione o sufixo "EventArgs".|
|`System.Enum`|❌NÃO derivar desta classe; use a palavra-chave suportada pelo seu idioma; por exemplo, em C#, use a `enum` palavra-chave.<br /><br /> ❌NÃO adicione o sufixo "Enum" ou "Flag".|
|`System.Exception`|✔️ DO adicione o sufixo "Exceção".|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|✔️ DO adicione o sufixo "Dicionário". Note `IDictionary` que é um tipo específico de coleção, mas esta diretriz tem precedência sobre as diretrizes de coleta mais gerais que se segue.|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|✔️ DO adicione o sufixo "Collection".|
|`System.IO.Stream`|✔️ DO adicione o sufixo "Stream".|
|`CodeAccessPermission IPermission`|✔️ DO adicione o sufixo "Permissão".|

## <a name="naming-enumerations"></a>Nomeando Enumerações
 Os nomes dos tipos de enumeração (também chamados enums) em geral devem seguir as regras padrão de nomeação de tipo (PascalCasing, etc.). No entanto, existem diretrizes adicionais que se aplicam especificamente aos enums.

 ✔️ USO de um nome de tipo singular para uma enumeração, a menos que seus valores sejam campos de bits.

 ✔️ DO use um nome de tipo plural para uma enumeração com campos de bit como valores, também chamado de enum bandeiras.

 ❌NÃO use um sufixo "Enum" em nomes do tipo enum.

 ❌NÃO use sufixos "Bandeiras" ou "Bandeiras" em nomes de tipo enum.

 ❌NÃO use um prefixo em nomes de valorde enumeração (por exemplo, "ad" para enums ADO, "rtf" para enums de texto rico, etc.).

 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*

 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*

## <a name="see-also"></a>Confira também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
