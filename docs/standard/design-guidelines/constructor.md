---
title: Design do construtor
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- parameterless constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
author: KrzysztofCwalina
ms.openlocfilehash: a43ec815275e58f4bc6462fb4f5cb4733267de31
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972111"
---
# <a name="constructor-design"></a>Design do construtor

Há dois tipos de construtores: construtores de tipo e construtores de instância.

Construtores de tipo são estáticos e são executados pelo CLR antes de o tipo ser usado. Os construtores de instância são executados quando uma instância de um tipo é criada.

Construtores de tipo não podem usar parâmetros. Construtores de instância podem. Os construtores de instância que não usam parâmetros geralmente são chamados de construtores sem parâmetros.

Os construtores são a maneira mais natural de criar instâncias de um tipo. A maioria dos desenvolvedores pesquisará e tentará usar um Construtor antes que eles considerem maneiras alternativas de criar instâncias (como métodos de fábrica).

**✓ CONSIDER** fornecendo simples, idealmente padrão, construtores.

Um Construtor simples tem um número muito pequeno de parâmetros e todos os parâmetros são primitivos ou enums. Esses construtores simples aumentam a usabilidade da estrutura.

**✓ CONSIDER** usando um método de fábrica estáticos em vez de um construtor, se a semântica da operação desejada não é mapeados diretamente para a construção de uma nova instância, ou se seguir as diretrizes de design do construtor parece não natural.

**✓ DO** usar os parâmetros do construtor como atalhos para definir as propriedades principais.

Não deve haver nenhuma diferença na semântica entre o uso do construtor vazio seguido por alguns conjuntos de propriedades e o uso de um construtor com vários argumentos.

**✓ DO** usar o mesmo nome para os parâmetros do construtor e uma propriedade se os parâmetros do construtor são usados simplesmente definir a propriedade.

A única diferença entre esses parâmetros e as propriedades deve estar entre maiúsculas e minúsculas.

**✓ DO** mínimo de trabalho no construtor.

Os construtores não devem fazer muito trabalho além de capturar os parâmetros do construtor. O custo de qualquer outro processamento deve ser atrasado até que seja necessário.

**✓ DO** lançar exceções a partir de construtores de instância, se apropriado.

**✓** Declare explicitamente o construtor público sem parâmetros em classes, se esse construtor for necessário.

Se você não declarar explicitamente nenhum construtor em um tipo, muitas linguagens (como C#) adicionarão automaticamente um construtor público sem parâmetros. (Classes abstratas obtêm um construtor protegido.)

Adicionar um construtor com parâmetros a uma classe impede que o compilador adicione o construtor sem parâmetros. Isso geralmente causa alterações de interrupção acidentais.

**X Evite** definir construtores sem parâmetros explicitamente em structs.

Isso torna a criação de matriz mais rápida, porque se o construtor sem parâmetros não estiver definido, ele não precisará ser executado em todos os slots na matriz. Observe que muitos compiladores, incluindo C#, não permitem que structs tenham construtores sem parâmetros por esse motivo.

**X AVOID** chamando membros virtuais em um objeto dentro de seu construtor.

Chamar um membro virtual fará com que a substituição mais derivada seja chamada, mesmo que o construtor do tipo mais derivado ainda não tenha sido totalmente executado.

## <a name="type-constructor-guidelines"></a>Diretrizes de construtor de tipo

**✓ DO** tornar construtores estáticos em particular.

Um construtor estático, também chamado de construtor de classe, é usado para inicializar um tipo. O CLR chama o construtor estático antes que a primeira instância do tipo seja criada ou quaisquer membros estáticos nesse tipo sejam chamados. O usuário não tem controle sobre quando o construtor estático é chamado. Se um construtor estático não for privado, ele poderá ser chamado por um código diferente do CLR. Dependendo das operações executadas no construtor, isso pode causar um comportamento inesperado. O C# compilador força os construtores estáticos a serem privados.

**X DO NOT** lançar exceções a partir de construtores estáticos.

Se uma exceção for gerada de um construtor de tipo, o tipo não poderá ser usado no domínio do aplicativo atual.

**✓ CONSIDER** inicializar campos estáticos embutido em vez de usar explicitamente construtores estáticos, porque o tempo de execução é capaz de otimizar o desempenho de tipos que não tem um construtor estático definido explicitamente.

*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*

*Reimpresso por permissão da Pearson Education, Inc. de [diretrizes de design de estrutura: Convenções, idiomas e padrões para bibliotecas .net reutilizáveis, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicadas em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*

## <a name="see-also"></a>Consulte também

- [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
