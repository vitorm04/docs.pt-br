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
ms.openlocfilehash: c9cb178e838aab99c22089b527a6bd2e86b325de
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727844"
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

 ✔️ Tente usar nomes de parâmetro descritivos para indicar o padrão usado por sobrecargas menores.

 ❌ evitar nomes de parâmetro com variação arbitrária em sobrecargas. Se um parâmetro em uma sobrecarga representa a mesma entrada que um parâmetro em outra sobrecarga, os parâmetros deverão ter o mesmo nome.

 ❌ evitar ser inconsistente na ordenação de parâmetros em Membros sobrecarregados. Os parâmetros com o mesmo nome devem aparecer na mesma posição em todas as sobrecargas.

 ✔️ fazer apenas a sobrecarga virtual mais longa (se a extensibilidade for necessária). Sobrecargas menores devem simplesmente chamar para uma sobrecarga mais longa.

 ❌ não use os modificadores `ref` ou `out` para sobrecarregar os membros.

 Alguns idiomas não podem resolver chamadas para sobrecargas como esta. Além disso, essas sobrecargas geralmente têm semânticas completamente diferentes e, provavelmente, não devem ser sobrecarregadas, mas dois métodos separados.

 ❌ não têm sobrecargas com parâmetros na mesma posição e tipos semelhantes, ainda com semânticas diferentes.

 ✔️ permitir que `null` sejam passados para argumentos opcionais.

 ✔️ usar a sobrecarga de membros em vez de definir membros com argumentos padrão.

 Os argumentos padrão não são compatíveis com CLS.

 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*

 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*

## <a name="see-also"></a>Consulte também

- [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
