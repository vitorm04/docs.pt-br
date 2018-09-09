---
title: Gerando exceções
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fbbe84811e3fa096b9e13c459143311bb75a198
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44225143"
---
# <a name="exception-throwing"></a>Gerando exceções
Diretrizes de exceções descritas nesta seção exigem uma boa definição do significado da falha de execução. Falha na execução ocorre sempre que um membro não pode fazer o que ele foi projetado para fazer (o que o nome do membro implica). Por exemplo, se o `OpenFile` método não pode retornar um identificador de arquivo aberto para o chamador, ele será considerado uma falha na execução.  
  
 A maioria dos desenvolvedores tornaram-se confortável usando exceções para erros de uso como a divisão por zero ou referências nulas. No Framework, as exceções são usadas para todas as condições de erro, incluindo erros de execução.  
  
 **X DO NOT** retornar códigos de erro.  
  
 As exceções são o principal meio de erros em estruturas de relatórios.  
  
 **✓ DO** falhas de execução de relatório por Lançando exceções.  
  
 **✓ CONSIDER** finalizando o processo chamando `System.Environment.FailFast` (recurso do .NET Framework 2.0) em vez de gerar uma exceção se o seu código encontrar uma situação em que não é seguro para execução ainda mais.  
  
 **X DO NOT** use exceções para o fluxo normal de controle, se possível.  
  
 Exceto para falhas de sistema e operações com condições de corrida potenciais, designers do framework devem projetar APIs para que os usuários podem escrever código que não lança exceções. Por exemplo, você pode fornecer uma maneira de verificar pré-condições antes de chamar um membro, para que os usuários podem escrever código que não lança exceções.  
  
 O membro usado para verificar pré-condições de outro membro é conhecido como um testador e o membro que realmente faz o trabalho é chamado um mal-intencionado.  
  
 Há casos em que o padrão de testador mal-intencionado pode ter uma sobrecarga de desempenho inaceitável. Nesses casos, deve ser considerado o padrão Try Parse chamados (consulte [exceções e desempenho](../../../docs/standard/design-guidelines/exceptions-and-performance.md) para obter mais informações).  
  
 **✓ CONSIDER** as implicações de desempenho de Lançando exceções. Acima de 100 por segundo as taxas de throw têm probabilidade de afetar visivelmente o desempenho da maioria dos aplicativos.  
  
 **✓ DO** documento todas as exceções lançadas por membros publicamente acessível devido a uma violação do membro (em vez de uma falha do sistema) do contrato e tratá-los como parte de seu contrato.  
  
 As exceções que são uma parte do contrato não devem alterar de uma versão para a próxima (ou seja, não deve alterar o tipo de exceção e não devem ser adicionadas a novas exceções).  
  
 **X DO NOT** tem membros públicos que podem ou throw ou não com base em alguma opção.  
  
 **X DO NOT** tem membros públicos que retornam exceções como o valor de retorno ou um `out` parâmetro.  
  
 Retornando as exceções de APIs públicas, em vez de lançá-las frustra muitos dos benefícios dos relatórios de exceção com base no erro.  
  
 **✓ CONSIDER** usando métodos de construtor de exceção.  
  
 É comum para lançar a mesma exceção de locais diferentes. Para evitar o inchaço de código, use os métodos auxiliares que criam exceções e inicializam suas propriedades.  
  
 Além disso, os membros que lançam exceções não estiverem embutidos. Mover a instrução throw dentro do construtor pode permitir que o membro ser embutida.  
  
 **X DO NOT** lançam exceções em blocos de filtro de exceção.  
  
 Quando um filtro de exceção gera uma exceção, a exceção é capturada pelo CLR e o filtro retorna false. Esse comportamento é indistinguível do filtro de execução e retornando false explicitamente e, portanto, é muito difícil de depurar.  
  
 **X AVOID** explicitamente Lançando exceções a partir de blocos finally. Exceções implicitamente geradas resultante da chamada de métodos que lançam são aceitáveis.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
- [Diretrizes de design para exceções](../../../docs/standard/design-guidelines/exceptions.md)
