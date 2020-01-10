---
title: Gerar exceções
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: 7d1b63e5fde57cbe37a1250d16b6bf74a2d5dc8e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709394"
---
# <a name="exception-throwing"></a>Gerar exceções
As diretrizes de lançamento de exceção descritas nesta seção exigem uma boa definição do significado da falha de execução. A falha de execução ocorre sempre que um membro não pode fazer o que foi projetado (o que o nome do membro implica). Por exemplo, se o método `OpenFile` não puder retornar um identificador de arquivo aberto para o chamador, ele será considerado uma falha de execução.  
  
 A maioria dos desenvolvedores se sente confortável com o uso de exceções para erros de uso, como divisão por zero ou referências nulas. Na estrutura, as exceções são usadas para todas as condições de erro, incluindo erros de execução.  
  
 **X DO NOT** retornar códigos de erro.  
  
 As exceções são os principais meios de relatar erros em estruturas.  
  
 **✓ DO** falhas de execução de relatório por Lançando exceções.  
  
 **✓ CONSIDER** finalizando o processo chamando `System.Environment.FailFast` (recurso do .NET Framework 2.0) em vez de gerar uma exceção se o seu código encontrar uma situação em que não é seguro para execução ainda mais.  
  
 **X DO NOT** use exceções para o fluxo normal de controle, se possível.  
  
 Exceto para falhas do sistema e operações com possíveis condições de corrida, os designers de estrutura devem criar APIs para que os usuários possam escrever código que não gere exceções. Por exemplo, você pode fornecer uma maneira de verificar as pré-condições antes de chamar um membro para que os usuários possam escrever código que não gere exceções.  
  
 O membro usado para verificar as pré-condições de outro membro é geralmente chamado de testador, e o membro que realmente faz o trabalho é chamado de doer.  
  
 Há casos em que o padrão do testador-doer pode ter uma sobrecarga de desempenho inaceitável. Nesses casos, o chamado padrão de teste de tentativa-análise deve ser considerado (consulte [exceções e desempenho](../../../docs/standard/design-guidelines/exceptions-and-performance.md) para obter mais informações).  
  
 **✓ CONSIDER** as implicações de desempenho de Lançando exceções. As taxas de geração acima de 100 por segundo provavelmente afetarão notavelmente o desempenho da maioria dos aplicativos.  
  
 **✓ DO** documento todas as exceções lançadas por membros publicamente acessível devido a uma violação do membro (em vez de uma falha do sistema) do contrato e tratá-los como parte de seu contrato.  
  
 As exceções que fazem parte do contrato não devem ser alteradas de uma versão para a seguinte (isto é, o tipo de exceção não deve ser alterado e novas exceções não devem ser adicionadas).  
  
 **X DO NOT** tem membros públicos que podem ou throw ou não com base em alguma opção.  
  
 **X DO NOT** tem membros públicos que retornam exceções como o valor de retorno ou um `out` parâmetro.  
  
 Retornar exceções de APIs públicas em vez de lançá-las derrota muitos dos benefícios do relatório de erros baseado em exceção.  
  
 **✓ CONSIDER** usando métodos de construtor de exceção.  
  
 É comum lançar a mesma exceção de locais diferentes. Para evitar o excesso de código, use métodos auxiliares que criam exceções e inicializam suas propriedades.  
  
 Além disso, os membros que lançam exceções não estão ficando embutidos. Mover a instrução Throw dentro do construtor pode permitir que o membro seja embutido.  
  
 **X DO NOT** lançam exceções em blocos de filtro de exceção.  
  
 Quando um filtro de exceção gera uma exceção, a exceção é capturada pelo CLR e o filtro retorna falso. Esse comportamento é indistinguíveis do filtro executando e retornando false explicitamente e, portanto, é muito difícil de depurar.  
  
 **X AVOID** explicitamente Lançando exceções a partir de blocos finally. Exceções implicitamente geradas resultantes de métodos de chamada que geram são aceitáveis.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Veja também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de design para exceções](../../../docs/standard/design-guidelines/exceptions.md)
