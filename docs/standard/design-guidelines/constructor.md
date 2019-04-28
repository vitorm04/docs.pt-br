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
- default constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
author: KrzysztofCwalina
ms.openlocfilehash: 68192e3b75a120c73b82c34005d4dee650540bf3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925457"
---
# <a name="constructor-design"></a>Design do construtor
Há dois tipos dos construtores: construtores e construtores de instância de tipo.  
  
 Construtores de tipo são estáticos e são executados pelo CLR, antes do tipo é usado. Construtores de instância executados quando uma instância de um tipo é criada.  
  
 Construtores de tipo não podem receber quaisquer parâmetros. Construtores de instância podem. Construtores de instância que não usam todos os parâmetros são chamados de construtores padrão.  
  
 Construtores são a maneira mais natural para criar instâncias de um tipo. A maioria dos desenvolvedores pesquisará e tentar usar um construtor antes que eles considerarem maneiras alternativas de criação de instâncias (como métodos de fábrica).  
  
 **✓ CONSIDER** fornecendo simples, idealmente padrão, construtores.  
  
 Um construtor simple tem um número muito pequeno de parâmetros e todos os parâmetros são primitivos ou enumerações. Esses construtores simples aumentam a usabilidade do framework.  
  
 **✓ CONSIDER** usando um método de fábrica estáticos em vez de um construtor, se a semântica da operação desejada não é mapeados diretamente para a construção de uma nova instância, ou se seguir as diretrizes de design do construtor parece não natural.  
  
 **✓ DO** usar os parâmetros do construtor como atalhos para definir as propriedades principais.  
  
 Não deve haver nenhuma diferença semântica entre usando o construtor vazio seguido por alguns conjuntos de propriedade e um construtor com vários argumentos.  
  
 **✓ DO** usar o mesmo nome para os parâmetros do construtor e uma propriedade se os parâmetros do construtor são usados simplesmente definir a propriedade.  
  
 A única diferença entre esses parâmetros e as propriedades deve ser maiusculas e minúsculas.  
  
 **✓ DO** mínimo de trabalho no construtor.  
  
 Construtores não devem fazer muito trabalho que não seja captura os parâmetros do construtor. O custo de qualquer outro processamento deve ser atrasado até que o necessário.  
  
 **✓ DO** lançar exceções a partir de construtores de instância, se apropriado.  
  
 **✓ DO** declarar explicitamente o construtor padrão público em classes, se tal construtor for necessária.  
  
 Se você não declarar construtores explicitamente em um tipo, muitas linguagens (como c#) adiciona automaticamente um construtor padrão público. (As classes abstratas obterá um construtor protegido.)  
  
 Adicionando um construtor parametrizado a uma classe impede que o compilador adicione o construtor padrão. Com frequência isso causa alterações significativas acidental.  
  
 **X AVOID** explicitamente definir construtores padrão em estruturas.  
  
 Isso torna a criação de matriz rápida, porque se o construtor padrão não for definido, ele não tem que ser executado em cada slot na matriz. Observe que muitos compiladores, incluindo c#, não permitem structs ter construtores sem parâmetros por esse motivo.  
  
 **X AVOID** chamando membros virtuais em um objeto dentro de seu construtor.  
  
 Chamar um membro virtual fará com que a substituição mais derivada a ser chamado, mesmo se o construtor do tipo mais derivado não foi totalmente executado ainda.  
  
### <a name="type-constructor-guidelines"></a>Diretrizes do construtor de tipo  
 **✓ DO** tornar construtores estáticos em particular.  
  
 Um construtor estático, também chamado construtor de classe, é usado para inicializar um tipo. O CLR chama o construtor estático antes da primeira instância do tipo é criada ou quaisquer membros estáticos no tipo são chamados. O usuário não tem controle sobre quando o construtor estático é chamado. Se um construtor estático não for privado, ele pode ser chamado pelo código que não seja o CLR. Dependendo das operações realizadas no construtor, isso pode causar um comportamento inesperado. O compilador c# força construtores estáticos a ser privadas.  
  
 **X DO NOT** lançar exceções a partir de construtores estáticos.  
  
 Se uma exceção for gerada de um construtor de tipo, o tipo não é utilizável no domínio do aplicativo atual.  
  
 **✓ CONSIDER** inicializar campos estáticos embutido em vez de usar explicitamente construtores estáticos, porque o tempo de execução é capaz de otimizar o desempenho de tipos que não tem um construtor estático definido explicitamente.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
