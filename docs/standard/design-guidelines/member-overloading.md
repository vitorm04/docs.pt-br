---
title: Sobrecarga de membro
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
author: KrzysztofCwalina
ms.openlocfilehash: 4caa0ae78d168b23fd2862153bef0e3960d3ea42
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392952"
---
# <a name="member-overloading"></a>Sobrecarga de membro
Sobrecarga de membros significa criar dois ou mais membros no mesmo tipo que diferem apenas no número ou tipo de parâmetros, mas têm o mesmo nome. Por exemplo, no seguinte, o método `WriteLine` está sobrecarregado:  
  
```csharp  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 Como somente métodos, construtores e propriedades indexadas podem ter parâmetros, somente esses membros podem ser sobrecarregados.  
  
 A sobrecarga é uma das técnicas mais importantes para melhorar a usabilidade, a produtividade e a legibilidade de bibliotecas reutilizáveis. O sobrecarregamento no número de parâmetros torna possível fornecer versões mais simples de construtores e métodos. Sobrecarregar no tipo de parâmetro torna possível usar o mesmo nome de membro para membros que executam operações idênticas em um conjunto selecionado de tipos diferentes.  
  
 **✓ DO** tente usar nomes de parâmetro descritivo para indicar o padrão usado por sobrecargas mais curto.  
  
 **X AVOID** arbitrariamente diversos nomes de parâmetro em sobrecargas. Se um parâmetro em uma sobrecarga representa a mesma entrada que um parâmetro em outra sobrecarga, os parâmetros deverão ter o mesmo nome.  
  
 **X AVOID** inconsistentes na ordem de parâmetros na sobrecarga membros. Os parâmetros com o mesmo nome devem aparecer na mesma posição em todas as sobrecargas.  
  
 **✓ DO** fazer somente a maior sobrecarga virtual (se extensibilidade é necessária). Sobrecargas menores devem simplesmente chamar para uma sobrecarga mais longa.  
  
 **X DO NOT** usar `ref` ou `out` modificadores para sobrecarregar membros.  
  
 Alguns idiomas não podem resolver chamadas para sobrecargas como esta. Além disso, essas sobrecargas geralmente têm semânticas completamente diferentes e, provavelmente, não devem ser sobrecarregadas, mas dois métodos separados.  
  
 **X DO NOT** têm sobrecargas com parâmetros na mesma posição e tipos semelhantes, mas com semânticas diferentes.  
  
 **✓ DO** permitir `null` a serem passados para os argumentos opcionais.  
  
 **✓ DO** usar membro sobrecarga em vez de definir membros com argumentos padrão.  
  
 Os argumentos padrão não são compatíveis com CLS.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
