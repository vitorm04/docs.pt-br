---
title: "Métodos de extensão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 28ce4451f9f8cc634ab76b3b4ef845103ea55e35
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="extension-methods"></a>Métodos de extensão
Métodos de extensão são um recurso de linguagem que permite que os métodos estáticos ser chamado usando a sintaxe de chamada de método de instância. Esses métodos devem ter pelo menos um parâmetro, que representa a instância em que é o método operar.  
  
 A classe que define esses métodos de extensão é conhecida como a classe "Patrocinador", e ele deve ser declarado como estático. Para usar os métodos de extensão, uma deve importar o namespace de definição de classe patrocinador.  
  
 **X Evite** frivolously definir métodos de extensão, especialmente em tipos que você não possui.  
  
 Se você é proprietário de um tipo de código-fonte, considere o uso de métodos de instância regular. Se você não possui, e você deseja adicionar um método, tenha muito cuidado. Uso livre dos métodos de extensão tem o potencial de problemas de APIs de tipos que não foram projetados para que esses métodos.  
  
 **✓ CONSIDERE** usando métodos de extensão em qualquer um dos seguintes cenários:  
  
-   Para fornecer auxiliar funcionalidade relevante para cada implementação de uma interface, diz funcionalidade pode ser gravada em termos de interface principal. Isso ocorre porque as implementações concretas caso contrário, não podem ser atribuídas às interfaces. Por exemplo, o `LINQ to Objects` operadores são implementados como métodos de extensão para todos os <xref:System.Collections.Generic.IEnumerable%601> tipos. Portanto, qualquer `IEnumerable<>` implementação é habilitado automaticamente LINQ.  
  
-   Quando um método de instância introduz uma dependência em algum tipo, mas tal dependência interrompe as regras de gerenciamento de dependência. Por exemplo, uma dependência do <xref:System.String> para <xref:System.Uri?displayProperty=nameWithType> provavelmente não é desejável e isso `String.ToUri()` retornando do método de instância `System.Uri` seria o design incorreto de uma perspectiva de gerenciamento de dependência. Um método de extensão estático `Uri.ToUri(this string str)` retornando `System.Uri` seria um muito melhor design.  
  
 **X Evite** definir métodos de extensão em <xref:System.Object?displayProperty=nameWithType>.  
  
 Os usuários do VB não poderá chamar esses métodos em referências de objeto usando a sintaxe de método de extensão. VB não oferece suporte para chamar esses métodos porque, em VB, declarar uma referência como objeto força todas as invocações de método nele para atraso associado (chamado de membro real é determinado em tempo de execução), enquanto as associações para métodos de extensão são determinadas em tempo de compilação (antecipada vinculado).  
  
 Observe que a diretriz se aplica a outros idiomas em que o mesmo comportamento de associação está presente, ou onde não há suporte para métodos de extensão.  
  
 **X não** colocar os métodos de extensão no mesmo namespace que o tipo estendido, a menos que ele seja para a adição de métodos para interfaces de ou para o gerenciamento de dependência.  
  
 **X Evite** definir dois ou mais métodos de extensão com a mesma assinatura, mesmo que eles estejam em namespaces diferentes.  
  
 **✓ CONSIDERE** definir métodos de extensão no mesmo namespace que o tipo estendido se o tipo é uma interface e se os métodos de extensão devem ser usados na maioria dos casos.  
  
 **X não** definir métodos de extensão implementando um recurso nos namespaces normalmente associados com outros recursos. Em vez disso, defini-los no namespace associado com o recurso que eles pertencem.  
  
 **X Evite** genérico de nomenclatura de namespaces dedicado para métodos de extensão (por exemplo, "extensões"). Use um nome descritivo (por exemplo, "roteamento") em vez disso.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
