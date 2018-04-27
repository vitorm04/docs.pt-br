---
title: Lançando exceções
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 47c16ac94054fff193b1f5976fe7f04f10a39ecd
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="exception-throwing"></a>Lançando exceções
Lançando exceções diretrizes descritas nesta seção exigem uma definição válida do significado da falha de execução. Falha na execução ocorre sempre que um membro não é possível fazer o que ele foi projetado para fazer (o que o nome de membro implica). Por exemplo, se o `OpenFile` método não pode retornar um identificador de arquivo aberto ao chamador, ele será considerado uma falha na execução.  
  
 A maioria dos desenvolvedores tornaram-se familiarizado com o uso de exceções para erros de uso como a divisão por zero ou referências nulas. Na estrutura, as exceções são usadas para todas as condições de erro, incluindo erros de execução.  
  
 **X não** retornar códigos de erro.  
  
 As exceções são o principal meio de relatório de erros em estruturas.  
  
 **FAZER ✓** falhas de execução de relatório por Lançando exceções.  
  
 **✓ CONSIDERE** finalizando o processo chamando `System.Environment.FailFast` (recurso do .NET Framework 2.0) em vez de gerar uma exceção se o seu código encontrar uma situação em que não é seguro para execução ainda mais.  
  
 **X não** use exceções para o fluxo normal de controle, se possível.  
  
 Exceto para operações com condições de corrida potenciais e falhas de sistema, designers de estrutura devem projetar APIs para que os usuários podem gravar código que não lançam exceções. Por exemplo, você pode fornecer uma maneira de verificar pré-condições antes de chamar um membro para que os usuários podem gravar código que não lançam exceções.  
  
 O membro usado para verificar as pré-condições de outro membro é conhecido como um testador e o membro que realmente executa o trabalho é chamado um mal-intencionado.  
  
 Há casos em que o padrão de testador mal-intencionado pode ter uma sobrecarga de desempenho inaceitável. Nesses casos, o padrão de análise de tente chamados devem ser considerado (consulte [exceções e desempenho](../../../docs/standard/design-guidelines/exceptions-and-performance.md) para obter mais informações).  
  
 **✓ CONSIDERE** as implicações de desempenho de Lançando exceções. As taxas de throw acima de 100 por segundo estão provavelmente visivelmente afetar o desempenho da maioria dos aplicativos.  
  
 **FAZER ✓** documento todas as exceções lançadas por membros publicamente acessível devido a uma violação do membro (em vez de uma falha do sistema) do contrato e tratá-los como parte de seu contrato.  
  
 Exceções que fazem parte do contrato não devem alterar de uma versão para a próxima (ou seja, não deve alterar o tipo de exceção e não devem ser adicionadas novas exceções).  
  
 **X não** tem membros públicos que podem ou throw ou não com base em alguma opção.  
  
 **X não** tem membros públicos que retornam exceções como o valor de retorno ou um `out` parâmetro.  
  
 Retornando exceções de APIs públicas, em vez de lançá-las anula a muitos dos benefícios do relatório de erros com base em exceções.  
  
 **✓ CONSIDERE** usando métodos de construtor de exceção.  
  
 É comum para lançar a mesma exceção de diferentes locais. Para evitar inchaço de código, use os métodos auxiliares que criar exceções e inicializam suas propriedades.  
  
 Além disso, os membros que lançam exceções não estão obtendo embutida. Movendo a instrução throw dentro de construtor pode permitir que o membro a ser embutido.  
  
 **X não** lançam exceções em blocos de filtro de exceção.  
  
 Quando um filtro de exceção gera uma exceção, a exceção é capturada pelo CLR e o filtro retorna false. Esse comportamento não é possível distinguir do filtro de execução e retornar false explicitamente e, portanto, é muito difícil de depurar.  
  
 **X Evite** explicitamente Lançando exceções a partir de blocos finally. Exceções implicitamente geradas resultante da chamada de métodos que lançam são aceitáveis.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Diretrizes de design para exceções](../../../docs/standard/design-guidelines/exceptions.md)
