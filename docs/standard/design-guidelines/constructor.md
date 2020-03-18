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
ms.openlocfilehash: 7ab795cd4c6e0ff5e1451c05987848c41bd69577
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400599"
---
# <a name="constructor-design"></a>Design do construtor

Existem dois tipos de construtores: construtores de tipos e construtores de instâncias.

Os construtores de tipo são estáticos e são executados pela CLR antes do tipo ser usado. Construtores de instâncias são executados quando uma instância de um tipo é criada.

Os construtores de tipo não podem tomar parâmetros. Construtores de instâncias podem. Construtores de instâncias que não tomam parâmetros são frequentemente chamados de construtores sem parâmetros.

Os construtores são a maneira mais natural de criar instâncias de um tipo. A maioria dos desenvolvedores procurará e tentará usar um construtor antes de considerar formas alternativas de criar instâncias (como métodos de fábrica).

✔️ CONSIDEREm fornecer construtores simples, idealmente padrão.

Um simples construtor tem um número muito pequeno de parâmetros, e todos os parâmetros são primitivos ou enums. Tais construtores simples aumentam a usabilidade do quadro.

✔️ considerem usar um método de fábrica estática em vez de um construtor se a semântica da operação desejada não mapear diretamente para a construção de uma nova instância, ou se seguir as diretrizes de projeto do construtor não parecer natural.

✔️ DO use parâmetros de construção como atalhos para definir as propriedades principais.

Não deve haver diferença na semântica entre usar o construtor vazio seguido de alguns conjuntos de propriedades e usar um construtor com múltiplos argumentos.

✔️ DO use o mesmo nome para parâmetros de construção e uma propriedade se os parâmetros do construtor forem usados para simplesmente definir a propriedade.

A única diferença entre tais parâmetros e as propriedades deve ser o invólucro.

✔️ fazer o mínimo de trabalho na construtora.

Os construtores não devem fazer muito trabalho além de capturar os parâmetros do construtor. O custo de qualquer outro processamento deve ser adiado até que seja necessário.

✔️ DO lançar exceções de construtores de instâncias, se apropriado.

✔️ DO declarar explicitamente o construtor público sem parâmetros nas classes, se tal construtor for necessário.

Se você não declarar explicitamente nenhum construtor em um tipo, muitas línguas (como C#) adicionarão automaticamente um construtor sem parâmetros públicos. (Classes abstratas recebem um construtor protegido.)

Adicionar um construtor parametrizado a uma classe impede que o compilador adicione o construtor sem parâmetros. Isso muitas vezes causa mudanças acidentais.

❌EVITE definir explicitamente construtores sem parâmetros em estruturas.

Isso torna a criação de array mais rápida, porque se o construtor sem parâmetros não for definido, ele não precisa ser executado em todos os slots da matriz. Note que muitos compiladores, incluindo C#, não permitem que estruturas tenham construtores sem parâmetros por essa razão.

❌EVITE chamar membros virtuais em um objeto dentro de seu construtor.

Chamar um membro virtual fará com que a substituição mais derivada seja chamada, mesmo que o construtor do tipo mais derivado ainda não tenha sido totalmente executado.

## <a name="type-constructor-guidelines"></a>Diretrizes de Construção de Tipo

✔️ FAZEM construções estáticas privadas.

Um construtor estático, também chamado de construtor de classe, é usado para inicializar um tipo. O CLR chama o construtor estático antes que a primeira instância do tipo seja criada ou quaisquer membros estáticos desse tipo sejam chamados. O usuário não tem controle sobre quando o construtor estático é chamado. Se um construtor estático não for privado, ele pode ser chamado por código diferente do CLR. Dependendo das operações realizadas na construtora, isso pode causar comportamentos inesperados. O compilador C# força os construtores estáticos a serem privados.

❌NÃO jogue exceções de construtores estáticos.

Se uma exceção for lançada de um construtor de tipo, o tipo não poderá ser utilizável no domínio atual do aplicativo.

✔️ CONSIDEREMinicializar campos estáticos em linha em vez de usar explicitamente construtores estáticos, porque o tempo de execução é capaz de otimizar o desempenho de tipos que não possuem um construtor estático explicitamente definido.

*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*

*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*

## <a name="see-also"></a>Confira também

- [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
