---
title: Diretrizes de Design de tipo
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: 2a3cca0139974cbc92ce85a19db73dfb3d13d1a0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743572"
---
# <a name="type-design-guidelines"></a>Diretrizes de Design de tipo
Da perspectiva do CLR, há apenas duas categorias de tipos — tipos de referência e tipos de valor — mas, para fins de uma discussão sobre design de estrutura, dividimos os tipos em mais grupos lógicos, cada um com suas próprias regras de design específicas.

 As classes são o caso geral dos tipos de referência. Eles compõem a massa de tipos na maioria das estruturas. As classes conferem sua popularidade ao conjunto avançado de recursos orientados a objeto que dão suporte e à aplicabilidade geral. As classes base e as classes abstratas são grupos lógicos especiais relacionados à extensibilidade.

 Interfaces são tipos que podem ser implementados por tipos de referência e tipos de valor. Assim, eles podem servir como raízes de hierarquias polimórficas de tipos de referência e tipos de valor. Além disso, as interfaces podem ser usadas para simular várias heranças, o que não tem suporte nativo do CLR.

 As structs são o caso geral dos tipos de valor e devem ser reservadas para tipos pequenos e simples, semelhantes aos primitivos de linguagem.

 Enums são um caso especial de tipos de valor usados para definir conjuntos curtos de valores, como dias da semana, cores do console e assim por diante.

 Classes estáticas são tipos destinados a contêineres para membros estáticos. Normalmente, eles são usados para fornecer atalhos para outras operações.

 Delegados, exceções, atributos, matrizes e coleções são casos especiais de tipos de referência destinados a usos específicos, e as diretrizes para seu design e uso são discutidas em outro lugar neste livro.

 ✔️ garantir que cada tipo seja um conjunto bem definido de membros relacionados, não apenas uma coleção aleatória de funcionalidades não relacionadas.

## <a name="in-this-section"></a>Nesta seção
 [Escolher entre](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md) classes [abstratas](../../../docs/standard/design-guidelines/abstract-class.md) de classe e struct design da classe [estática](../../../docs/standard/design-guidelines/static-class.md) [design de](../../../docs/standard/design-guidelines/interface.md) design [struct](../../../docs/standard/design-guidelines/struct.md) [design de](../../../docs/standard/design-guidelines/enum.md) design de estrutura [tipos aninhados](../../../docs/standard/design-guidelines/nested-types.md) *partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*

 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*

## <a name="see-also"></a>Veja também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
