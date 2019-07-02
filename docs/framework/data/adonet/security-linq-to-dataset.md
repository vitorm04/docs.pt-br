---
title: Segurança (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
ms.openlocfilehash: 33af2200c5d672dc63dc7be79833a174bfe31c20
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504261"
---
# <a name="security-linq-to-dataset"></a>Segurança (LINQ to DataSet)
Este tópico discute problemas de segurança em LINQ to DataSet.  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>Passando uma consulta a um componente não confiável  
 Uma consulta LINQ to DataSet pode ser formulada em um ponto de um programa e executada em um diferente. No ponto em que a consulta é formulada, a consulta pode fazer referência a qualquer elemento que está visível nesse ponto, como membros particulares da classe à qual pertence o método de chamada ou símbolos que representam variáveis locais/argumentos. Em tempo de execução, a consulta poderá efetivamente acessar os membros que foram referenciados pela consulta em formulação, mesmo se o código de chamada não tem a visibilidade neles. O código que executa a consulta não tem visibilidade adicionada arbitrária, em que ele não é possível escolher o que acessar. Restrita poderá acessar o que a consulta acessa, e somente pela consulta própria.  
  
 Isso significa que passar uma referência a uma consulta para uma outra parte do código que o componente que recebe a consulta está sendo confiáveis com acesso a qualquer membros públicos e particulares que se refere a consulta. Em geral, consultas LINQ to DataSet não deve ser passado para componentes não confiáveis, a menos que a consulta é construída cuidadosamente para que ele não expõe informações que devem ser mantidas privadas.  
  
## <a name="external-input"></a>Entrada externo  
 Os aplicativos geralmente têm externo (a entrada de um usuário ou outro agente externa) e executar ações com base na entrada.  No caso do LINQ to DataSet, o aplicativo pode construir uma consulta de uma determinada maneira, com base na entrada externo ou usar a entrada na consulta externo. Consultas LINQ to DataSet aceitam parâmetros everywhere literais são aceitos. Desenvolvedores de aplicativos devem usar consultas parametrizadas, em vez da o injetar literais de um agente externo diretamente na consulta.  
  
 Qualquer entrada direta ou indiretamente derivado de usuário ou um agente externa pode ter o conteúdo que aproveita a sintaxe de linguagem de destino para executar ações desautorizadas. Isso é conhecido como um ataque de injeção SQL, chamado depois que um padrão de ataque onde o idioma de destino é Transact-SQL. A entrada do usuário injetada diretamente na consulta é usada para soltar uma tabela de base de dados, causa uma negação de serviço, ou caso contrário alterar a natureza da operação que está sendo executada. Embora a composição de consulta é possível no LINQ to DataSet, ela é executada por meio da API de modelo de objeto. Consultas LINQ to DataSet não são compostos por meio de manipulação de cadeia de caracteres ou concatenação, como elas estão em Transact-SQL e não são suscetíveis a ataques de injeção de SQL no sentido tradicional.  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
