---
title: Nomes de Classes, estruturas e Interfaces
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a4f4b9e48587138f3e65c0c6825af0b3e4e8c592
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-classes-structs-and-interfaces"></a>Nomes de Classes, estruturas e Interfaces
As diretrizes de nomenclatura que sigam se aplicam a nomenclatura do tipo geral.  
  
 **FAZER ✓** nome classes e estruturas com substantivos e frases nominais, usando PascalCasing.  
  
 Isso distingue os nomes de tipo de métodos que são nomeados com expressões de verbo.  
  
 **FAZER ✓** nome interfaces adjetivas frases ou ocasionalmente com substantivos e frases nominais.  
  
 Substantivos e frases nominais raramente devem ser usados e podem indicar que o tipo deve ser uma classe abstrata e não uma interface.  
  
 **X não** dar nomes de classe um prefixo (por exemplo, "C").  
  
 **✓ CONSIDERE** encerrar o nome de classes derivadas com o nome de classe base.  
  
 Isso é muito legível e explica a relação claramente. Alguns exemplos de código são: `ArgumentOutOfRangeException`, que é um tipo de `Exception`, e `SerializableAttribute`, que é um tipo de `Attribute`. No entanto, é importante usar razoável julgamento na aplicação dessa diretriz; Por exemplo, o `Button` classe é um tipo de `Control` evento, embora `Control` não aparecem em seu nome.  
  
 **FAZER ✓** nomes de interface de prefixo com a letra que, para indicar que o tipo é uma interface.  
  
 Por exemplo, `IComponent` (substantivo descritivo) `ICustomAttributeProvider` (locução), e `IPersistable` (adjetivo) são nomes de interface apropriada. Assim como acontece com outros nomes de tipo, evite abreviações.  
  
 **FAZER ✓** Certifique-se de que os nomes diferem somente por "I" prefixo no nome da interface quando você está definindo um par de classe – interface em que a classe é uma implementação padrão da interface.  
  
## <a name="names-of-generic-type-parameters"></a>Nomes de parâmetros de tipo genérico  
 Genéricos foram adicionados ao .NET Framework 2.0. O recurso introduzido um novo tipo de identificador chamado *parâmetro de tipo*.  
  
 **FAZER ✓** nome parâmetros de tipo genérico com nomes descritivos, a menos que o nome de um única letra é totalmente auto-explicativo e um nome descritivo não seria adicionar valor.  
  
 **✓ CONSIDERE** usando `T` como o nome do parâmetro de tipo para tipos com um parâmetro de tipo de letra único.  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **FAZER ✓** prefixo nomes de parâmetro de tipo descritivo com `T`.  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession{  
    TSession Session { get; }  
}  
```  
  
 **✓ CONSIDERE** indicando a restrições colocadas em um parâmetro de tipo no nome do parâmetro.  
  
 Por exemplo, um parâmetro é restrito a `ISession` pode ser chamado `TSession`.  
  
## <a name="names-of-common-types"></a>Nomes dos tipos comuns  
 **FAZER ✓** siga as diretrizes descritas na tabela a seguir ao nomear tipos derivados de ou implementar certos tipos do .NET Framework.  
  
|Tipo de base|Diretriz de tipo derivado/implementação|  
|---------------|------------------------------------------|  
|`System.Attribute`|**FAZER ✓** adicionar o sufixo "Atributo" em nomes de classes de atributos personalizados.|  
|`System.Delegate`|**FAZER ✓** adicionar o sufixo "EventHandler" em nomes de representantes que são usados em eventos.<br /><br /> **FAZER ✓** adicionar o sufixo "Retorno de chamada" para nomes de representantes de diferentes dos usados como manipuladores de eventos.<br /><br /> **X não** adicionar o sufixo "Representante" a um delegado.|  
|`System.EventArgs`|**FAZER ✓** adicionar o sufixo "EventArgs".|  
|`System.Enum`|**X não** derivar desta classe; use a palavra-chave com suporte em vez disso, o idioma; por exemplo, no c#, use o `enum` palavra-chave.<br /><br /> **X não** adicionar o sufixo "Enum" ou "Sinalizador".|  
|`System.Exception`|**FAZER ✓** adicionar o sufixo "Exception".|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**FAZER ✓** adicionar o sufixo "Dicionário". Observe que `IDictionary` é um tipo específico da coleção, mas essa diretriz tem precedência sobre a orientação mais geral de coleções que segue.|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**FAZER ✓** adicionar o sufixo "Coleção".|  
|`System.IO.Stream`|**FAZER ✓** adicionar o sufixo "Fluxo".|  
|`CodeAccessPermission IPermission`|**FAZER ✓** adicionar o sufixo "Permissão".|  
  
## <a name="naming-enumerations"></a>Enumerações de nomenclatura  
 Nomes de tipos de enumeração (também chamados de enums) em geral devem seguir as padrão de nomenclatura do tipo de regras (PascalCasing, etc.). No entanto, há diretrizes adicionais que se aplicam especificamente para enums.  
  
 **FAZER ✓** usar um nome de tipo singular para uma enumeração, a menos que seus valores são os campos de bits.  
  
 **FAZER ✓** usar um nome de tipo no plural para uma enumeração com campos de bits como valores, também chamados de enum de sinalizadores.  
  
 **X não** use um sufixo "Enum" em nomes de tipo de enum.  
  
 **X não** usar "Sinalizador" ou nomes de tipo sufixos "Sinalizadores" em enum.  
  
 **X não** usar um prefixo nos nomes de valor de enumeração (por exemplo, "ad" para ADO enums.), "rtf" para enums RTF, etc.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
