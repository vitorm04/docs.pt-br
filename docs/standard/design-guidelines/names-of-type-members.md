---
title: Nomes de membros de tipo
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6584eecb2df652f12fd14710bb5f15933aead541
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="names-of-type-members"></a>Nomes de membros de tipo
São feitas tipos de membros: métodos, propriedades, eventos, construtores e campos. As seções a seguir descrevem as diretrizes de nomeação de membros de tipo.  
  
## <a name="names-of-methods"></a>Nomes de métodos  
 Como os métodos são os meios de executar uma ação, as diretrizes de design requerem que os nomes de método verbos ou frases de verbo. Seguir essa orientação também serve para distinguir os nomes de método de nomes de propriedade e o tipo, que são frases nominais ou adjetivo.  
  
 **FAZER ✓** atribuir nomes de métodos que são verbos ou frases de verbo.  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a>Nomes de propriedades  
 Ao contrário de outros membros, propriedades devem ser dadas locução ou nomes de adjetivo. Isso ocorre porque uma propriedade refere-se aos dados e o nome da propriedade reflete que. PascalCasing sempre é usado para nomes de propriedade.  
  
 **FAZER ✓** propriedades usando um substantivo, locução ou adjetivo nomes.  
  
 **X não** têm propriedades que correspondem ao nome de "Get" métodos como no exemplo a seguir:  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 Esse padrão geralmente indica que a propriedade deve ser realmente um método.  
  
 **FAZER ✓** nome propriedades de coleção com plural frase que descreve os itens na coleção em vez de usar uma frase singular seguida por "List" ou "Coleção".  
  
 **FAZER ✓** nome propriedades Boolianas com uma frase afirmativa (`CanSeek` em vez de `CantSeek`). Opcionalmente, você também poderá colocar propriedades Boolianas com "É", "pode" ou "Tem", mas somente quando ele agrega valor.  
  
 **✓ CONSIDERE** fornecendo uma propriedade o mesmo nome de seu tipo.  
  
 Por exemplo, a seguinte propriedade corretamente obtém e define um valor de enumeração denominado `Color`, portanto, a propriedade é denominada `Color`:  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a>Nomes de eventos  
 Sempre consultem eventos alguma ação, que está acontecendo ou que ocorreu. Portanto, como com métodos, eventos são nomeados com verbos e indicativo de verbo é usado para indicar o momento quando o evento é gerado.  
  
 **FAZER ✓** nome eventos com um verbo ou uma frase de verbo.  
  
 Os exemplos incluem `Clicked`, `Painting`, `DroppedDown`e assim por diante.  
  
 **FAZER ✓** atribuir nomes de eventos com um conceito de antes e depois, usando o presente e tempos de passado.  
  
 Por exemplo, um evento de fechamento é gerado antes de fechar uma janela será chamado `Closing`, e que é gerado depois que a janela for fechada será chamado `Closed`.  
  
 **X não** usar "Antes" ou "Depois" prefixos ou postfixes para indicar pré e pós-eventos. Use presente e tempos de passado como acabou de ser descrita.  
  
 **FAZER ✓** nome manipuladores de eventos (delegados são usados como tipos de eventos) com o sufixo "EventHandler", conforme mostrado no exemplo a seguir:  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **FAZER ✓** usa dois parâmetros nomeados `sender` e `e` em manipuladores de eventos.  
  
 O parâmetro do remetente representa o objeto que gerou o evento. O parâmetro do remetente normalmente é do tipo `object`, mesmo que seja possível usar um tipo mais específico.  
  
 **FAZER ✓** nome do evento de classes de argumento com o sufixo "EventArgs".  
  
## <a name="names-of-fields"></a>Nomes de campos  
 As diretrizes de nomenclatura de campo se aplicam a campos protegidos e públicos estáticos. Campos internos e privados não são cobertos pelas diretrizes e campos de instância público ou protegido não são permitidos pelo [diretrizes de design do membro](../../../docs/standard/design-guidelines/member.md).  
  
 **FAZER ✓** use PascalCasing em nomes de campo.  
  
 **FAZER ✓** nome campos usando um substantivo, locução ou adjetivo.  
  
 **X não** use um prefixo para nomes de campo.  
  
 Por exemplo, não use "g _" ou "s _" para indicar campos estáticos.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
