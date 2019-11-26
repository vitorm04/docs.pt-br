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
author: KrzysztofCwalina
ms.openlocfilehash: 2ecd708ccb8eb91270e8ef9c174b8d7e599a2629
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353710"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Nomes de classes, structs e interfaces
As diretrizes de nomenclatura a seguir se aplicam à nomenclatura de tipo geral.  
  
 **✓ DO** nome classes e estruturas com substantivos e frases nominais, usando PascalCasing.  
  
 Isso distingue nomes de tipos de métodos, que são nomeados com frases de verbo.  
  
 **✓ DO** nome interfaces adjetivas frases ou ocasionalmente com substantivos e frases nominais.  
  
 As frases de substantivo e substantivo devem ser usadas raramente e podem indicar que o tipo deve ser uma classe abstrata, e não uma interface.  
  
 **X DO NOT** dar nomes de classe um prefixo (por exemplo, "C").  
  
 **✓ CONSIDER** encerrar o nome de classes derivadas com o nome de classe base.  
  
 Isso é muito legível e explica a relação claramente. Alguns exemplos disso no código são: `ArgumentOutOfRangeException`, que é um tipo de `Exception`e `SerializableAttribute`, que é um tipo de `Attribute`. No entanto, é importante usar o julgamento razoável na aplicação dessa diretriz; por exemplo, a classe `Button` é um tipo de evento de `Control`, embora `Control` não apareça em seu nome.  
  
 **✓ DO** nomes de interface de prefixo com a letra que, para indicar que o tipo é uma interface.  
  
 Por exemplo, `IComponent` (substantivo descritivo), `ICustomAttributeProvider` (substantivo, frase) e `IPersistable` (adjetivo) são nomes de interface apropriados. Assim como ocorre com outros nomes de tipo, evite abreviações.  
  
 **✓ DO** Certifique-se de que os nomes diferem somente por "I" prefixo no nome da interface quando você está definindo um par de classe – interface em que a classe é uma implementação padrão da interface.  
  
## <a name="names-of-generic-type-parameters"></a>Nomes de parâmetros de tipo genérico  
 Os genéricos foram adicionados ao .NET Framework 2,0. O recurso introduziu um novo tipo de identificador chamado *parâmetro de tipo*.  
  
 **✓ DO** nome parâmetros de tipo genérico com nomes descritivos, a menos que o nome de um única letra é totalmente auto-explicativo e um nome descritivo não seria adicionar valor.  
  
 **✓ CONSIDER** usando `T` como o nome do parâmetro de tipo para tipos com um parâmetro de tipo de letra único.  
  
```csharp  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ DO** prefixo nomes de parâmetro de tipo descritivo com `T`.  
  
```csharp  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 **✓ CONSIDER** indicando a restrições colocadas em um parâmetro de tipo no nome do parâmetro.  
  
 Por exemplo, um parâmetro restrito a `ISession` pode ser chamado `TSession`.  
  
## <a name="names-of-common-types"></a>Nomes de tipos comuns  
 **✓ DO** siga as diretrizes descritas na tabela a seguir ao nomear tipos derivados de ou implementar certos tipos do .NET Framework.  
  
|Tipo base|Diretriz de tipo derivado/implementando|  
|---------------|------------------------------------------|  
|`System.Attribute`|**✓ DO** adicionar o sufixo "Atributo" em nomes de classes de atributos personalizados.|  
|`System.Delegate`|**✓ DO** adicionar o sufixo "EventHandler" em nomes de representantes que são usados em eventos.<br /><br /> **✓ DO** adicionar o sufixo "Retorno de chamada" para nomes de representantes de diferentes dos usados como manipuladores de eventos.<br /><br /> **X DO NOT** adicionar o sufixo "Representante" a um delegado.|  
|`System.EventArgs`|**✓ DO** adicionar o sufixo "EventArgs".|  
|`System.Enum`|**X DO NOT** derivar desta classe; use a palavra-chave com suporte em vez disso, o idioma; por exemplo, no c#, use o `enum` palavra-chave.<br /><br /> **X DO NOT** adicionar o sufixo "Enum" ou "Sinalizador".|  
|`System.Exception`|**✓ DO** adicionar o sufixo "Exception".|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ DO** adicionar o sufixo "Dicionário". Observe que `IDictionary` é um tipo específico de coleção, mas essa diretriz tem precedência sobre a diretriz de coleções mais gerais a seguir.|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ DO** adicionar o sufixo "Coleção".|  
|`System.IO.Stream`|**✓ DO** adicionar o sufixo "Fluxo".|  
|`CodeAccessPermission IPermission`|**✓ DO** adicionar o sufixo "Permissão".|  
  
## <a name="naming-enumerations"></a>Enumerações de nomenclatura  
 Os nomes dos tipos de enumeração (também chamados de enums) em geral devem seguir as regras de nomenclatura de tipo padrão (PascalCasing, etc.). No entanto, há diretrizes adicionais que se aplicam especificamente a enums.  
  
 **✓ DO** usar um nome de tipo singular para uma enumeração, a menos que seus valores são os campos de bits.  
  
 **✓ DO** usar um nome de tipo no plural para uma enumeração com campos de bits como valores, também chamados de enum de sinalizadores.  
  
 **X DO NOT** use um sufixo "Enum" em nomes de tipo de enum.  
  
 **X DO NOT** usar "Sinalizador" ou nomes de tipo sufixos "Sinalizadores" em enum.  
  
 **X DO NOT** usar um prefixo nos nomes de valor de enumeração (por exemplo, "ad" para ADO enums.), "rtf" para enums RTF, etc.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
