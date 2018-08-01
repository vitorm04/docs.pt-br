---
title: Design do construtor
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d7ca279dc1626cd526910af93326280bcd8301d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575551"
---
# <a name="constructor-design"></a>Design do construtor
Há dois tipos de construtores: digite construtores e construtores de instância.  
  
 Construtores de tipo são estáticos e são executados pelo CLR, antes que o tipo é usado. Construtores de instância executados quando uma instância de um tipo é criada.  
  
 Construtores de tipo não usam nenhum parâmetro. Construtores de instância podem. Construtores de instância que não usam todos os parâmetros são chamados de construtores padrão.  
  
 Construtores são a maneira mais natural para criar instâncias de um tipo. A maioria dos desenvolvedores pesquisará e tentar usar um construtor antes de eles considerarem maneiras alternativas de criar instâncias (como métodos de fábrica).  
  
 **✓ CONSIDER** fornecendo simples, idealmente padrão, construtores.  
  
 Um construtor simple tem um número muito pequeno de parâmetros, e todos os parâmetros são primitivos ou enums. Tais construtores simples aumentam a usabilidade do framework.  
  
 **✓ CONSIDER** usando um método de fábrica estáticos em vez de um construtor, se a semântica da operação desejada não é mapeados diretamente para a construção de uma nova instância, ou se seguir as diretrizes de design do construtor parece não natural.  
  
 **✓ DO** usar os parâmetros do construtor como atalhos para definir as propriedades principais.  
  
 Não deve haver nenhuma diferença na semântica entre usando o construtor vazio seguido por alguns conjuntos de propriedades e usar um construtor com vários argumentos.  
  
 **✓ DO** usar o mesmo nome para os parâmetros do construtor e uma propriedade se os parâmetros do construtor são usados simplesmente definir a propriedade.  
  
 A única diferença entre esses parâmetros e as propriedades deve ser maiusculas e minúsculas.  
  
 **✓ DO** mínimo de trabalho no construtor.  
  
 Construtores não devem fazer muito trabalho diferente de captura os parâmetros do construtor. O custo de qualquer outro processamento deve ser atrasado até que o necessário.  
  
 **✓ DO** lançar exceções a partir de construtores de instância, se apropriado.  
  
 **✓ DO** declarar explicitamente o construtor padrão público em classes, se tal construtor for necessária.  
  
 Se você não declarar explicitamente nenhum construtor em um tipo, muitos idiomas (como c#) adicionará automaticamente um construtor padrão público. (Classes abstratas obtém um construtor protegido.)  
  
 Adicionar um construtor com parâmetros para uma classe impede que o compilador adicione o construtor padrão. Isso geralmente faz com que as alterações recentes acidental.  
  
 **X AVOID** explicitamente definir construtores padrão em estruturas.  
  
 Isso torna a criação de matriz rápida, porque se o construtor padrão não for definido, ele não tem que ser executado em cada slot na matriz. Observe que muitos compiladores, incluindo c#, não permitem estruturas ter construtores sem parâmetros por esse motivo.  
  
 **X AVOID** chamando membros virtuais em um objeto dentro de seu construtor.  
  
 Chamar um membro virtual fará com que a substituição mais derivada a ser chamado, mesmo se o construtor do tipo mais derivado não foi totalmente executado ainda.  
  
### <a name="type-constructor-guidelines"></a>Diretrizes do construtor de tipo  
 **✓ DO** tornar construtores estáticos em particular.  
  
 Um construtor estático, também chamado de um construtor de classe é usado para inicializar um tipo. O CLR chama o construtor estático antes da primeira instância do tipo é criada ou é chamado de qualquer membro estático nesse tipo. O usuário não tem controle sobre quando o construtor estático é chamado. Se um construtor estático não é privado, ele pode ser chamado pelo código que não seja o CLR. Dependendo de operações executadas no construtor, isso pode causar um comportamento inesperado. O compilador c# força construtores estáticos ser particulares.  
  
 **X DO NOT** lançar exceções a partir de construtores estáticos.  
  
 Se uma exceção é gerada de um construtor de tipo, o tipo não é utilizável no domínio do aplicativo atual.  
  
 **✓ CONSIDER** inicializar campos estáticos embutido em vez de usar explicitamente construtores estáticos, porque o tempo de execução é capaz de otimizar o desempenho de tipos que não tem um construtor estático definido explicitamente.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
