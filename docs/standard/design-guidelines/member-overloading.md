---
title: Sobrecarga de membro
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2127497d294cbfd4e1bb24d033f432378627ff13
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353168"
---
# <a name="member-overloading"></a>Sobrecarga de membro
Sobrecarga de membro significa criar dois ou mais membros no mesmo tipo que diferem somente no número ou tipo de parâmetros, mas que têm o mesmo nome. Por exemplo, em seguida, o `WriteLine` método está sobrecarregado:  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 Como apenas métodos, construtores e propriedades indexadas podem ter parâmetros, somente os membros podem ser sobrecarregados.  
  
 Sobrecarga é uma das técnicas mais importantes para melhorar a usabilidade, a produtividade e facilitar a leitura de bibliotecas reutilizáveis. Sobrecarregando o número de parâmetros torna possível fornecer versões mais simples dos construtores e métodos. Sobrecarga no tipo de parâmetro torna possível usar o mesmo nome de membro para executar operações idêntico em um conjunto selecionado de diferentes tipos de membros.  
  
 **✓ DO** tente usar nomes de parâmetro descritivo para indicar o padrão usado por sobrecargas mais curto.  
  
 **X AVOID** arbitrariamente diversos nomes de parâmetro em sobrecargas. Se um parâmetro em uma sobrecarga representa a mesma entrada como um parâmetro em outra sobrecarga, os parâmetros devem ter o mesmo nome.  
  
 **X AVOID** inconsistentes na ordem de parâmetros na sobrecarga membros. Parâmetros com o mesmo nome deverá aparecer na mesma posição em todas as sobrecargas.  
  
 **✓ DO** fazer somente a maior sobrecarga virtual (se extensibilidade é necessária). Sobrecargas mais curtas devem simplesmente chamar por meio de uma sobrecarga maior.  
  
 **X DO NOT** usar `ref` ou `out` modificadores para sobrecarregar membros.  
  
 Alguns idiomas não podem resolver chamadas para sobrecargas assim. Além disso, essas sobrecargas geralmente têm semânticas completamente diferentes e provavelmente não devem ser sobrecargas, mas dois métodos separados em vez disso.  
  
 **X DO NOT** têm sobrecargas com parâmetros na mesma posição e tipos semelhantes, mas com semânticas diferentes.  
  
 **✓ DO** permitir `null` a serem passados para os argumentos opcionais.  
  
 **✓ DO** usar membro sobrecarga em vez de definir membros com argumentos padrão.  
  
 Argumentos padrão não estão em conformidade com CLS.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)  
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
