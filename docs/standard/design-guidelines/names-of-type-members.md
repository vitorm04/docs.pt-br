---
title: Nomes de membros de tipo
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
author: KrzysztofCwalina
ms.openlocfilehash: 7cf98b8ed1957352f357c7a9d580b4fd567a1634
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576935"
---
# <a name="names-of-type-members"></a>Nomes de membros de tipo
Tipos são compostos de membros: métodos, propriedades, eventos, construtores e campos. As seções a seguir descrevem as diretrizes de nomenclatura de membros de tipo.  
  
## <a name="names-of-methods"></a>Nomes de métodos  
 Como os métodos são os meios para executar uma ação, as diretrizes de design exigem que os nomes de métodos sejam verbos ou frases verbais. Seguir essa diretriz também serve para distinguir os nomes de métodos de nomes de propriedades e tipos, que são substantivos ou frases adjetivas.  
  
 **✓ DO** nomeie os métodos que são verbos ou frases verbais.  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a>Nomes de propriedades  
 Diferentemente de outros membros, as propriedades devem ser nomeadas com uma frase substantivada ou um adjetivo. Isso porque uma propriedade se refere a dados, e o nome da propriedade reflete isso. PascalCasing sempre é usado para nomes de propriedade.  
  
 **✓ DO** nomeie as propriedades usando um substantivo, uma frase substantivada ou um adjetivo.  
  
 **X DO NOT** não tenha propriedades que correspondam ao nome dos métodos "Get", como no exemplo a seguir:  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 Esse padrão geralmente indica que a propriedade deveria realmente ser um método.  
  
 **✓ DO** nomeie as propriedades de coleção com uma frase no plural que descreva os itens na coleção em vez de usar uma frase no singular seguida por "List" ou "Collection".  
  
 **✓ DO** nomeie as propriedades boolianas com uma frase afirmativa (`CanSeek` em vez de `CantSeek`). Opcionalmente, você também pode prefixar as propriedades boolianas com "Is", "Can" ou "Has", mas somente quando adicionar valor.  
  
 **✓ CONSIDER** nomeie uma propriedade com o mesmo nome de seu tipo.  
  
 Por exemplo, a seguinte propriedade obtém e define corretamente um valor de enumeração denominado `Color`, portanto, a propriedade é chamada `Color`:  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a>Nomes de eventos  
 Eventos sempre fazem referência a uma ação, seja uma ação que está acontecendo ou que já ocorreu. Portanto, assim como acontece com os métodos, os eventos são nomeados com verbos e o tempo verbal é usado para indicar o horário em que o evento é acionado.  
  
 **✓ DO** nomeie os eventos com um verbo ou uma frase verbal.  
  
 Os exemplos incluem `Clicked`, `Painting`, `DroppedDown`, etc.  
  
 **✓ DO** nomeie os eventos com um conceito de antes e depois, usando os tempos verbais Pretérito e Presente.  
  
 Por exemplo, um evento de fechamento gerado antes de uma janela ser fechada seria chamado de `Closing`, e um gerado após a janela ser fechada seria chamado de `Closed`.  
  
 **X DO NOT** não use os sufixos ou prefixos "Before" ou "After" para indicar eventos anteriores e posteriores. Use os tempos verbais Pretérito e Presente conforme descrito.  
  
 **✓ DO** nomeie manipuladores de eventos (delegados usados como tipos de eventos) com o sufixo "EventHandler", conforme mostrado no exemplo a seguir:  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **✓ DO** use dois parâmetros nomeados `sender` e `e` nos manipuladores de eventos.  
  
 O parâmetro do remetente representa o objeto que acionou o evento. O parâmetro do remetente normalmente é do tipo `object`, mesmo se for possível empregar um tipo mais específico.  
  
 **✓ DO** nomeie classes de argumento de evento com o sufixo "EventArgs".  
  
## <a name="names-of-fields"></a>Nomes de campos  
 As diretrizes de nomenclatura de campo se aplicam a campos públicos e protegidos estáticos. Campos particulares e internos não são cobertos pelas diretrizes, e campos de instância pública ou protegida não são permitidos pelas [diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md).  
  
 **✓ DO** use PascalCasing nos nomes de campos.  
  
 **✓ DO** nomeie os campos usando um substantivo, uma frase substantivada ou um adjetivo.  
  
 **X DO NOT** não use um prefixo para nomes de campos.  
  
 Por exemplo, não use "g_" ou "s_" para indicar campos estáticos.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
