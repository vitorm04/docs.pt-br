---
title: "Segurança (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 305ff1232b21def3c8e7dcb1bec529f81c4e701a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="security-linq-to-dataset"></a>Segurança (LINQ to DataSet)
Este tópico discute problemas de segurança em [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>Passando uma consulta a um componente não confiável  
 Um [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consulta pode ser formulada em um ponto de um programa e executada em um diferente. No ponto em que a consulta é formulada, a consulta pode fazer referência a qualquer elemento que é visível nesse ponto, como os membros particulares da classe à qual pertence o método de chamada ou símbolos que representam variáveis locais/argumentos. Em tempo de execução, a consulta poderá efetivamente acessar os membros que foram referenciados pela consulta em formulação, mesmo se o código de chamada não tem a visibilidade neles. O código que executa a consulta não tem visibilidade adicionada arbitrária, em que ele não é possível escolher o que acessem. Restrita poderá acessar o que a consulta acessa, e somente pela consulta própria.  
  
 Isso significa que passar uma referência a uma consulta para uma outra parte do código que o componente que recebe a consulta está sendo confiáveis com acesso a qualquer membros públicos e particulares que se refere a consulta. Em geral, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consultas não devem ser passadas para componentes não confiáveis, a menos que a consulta foi cuidadosamente construída para que ele não expõe informações que devem ser mantidas em particulares.  
  
## <a name="external-input"></a>Entrada externo  
 Os aplicativos geralmente têm externo (a entrada de um usuário ou outro agente externa) e executar ações com base na entrada.  No caso de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], o aplicativo pode construir uma consulta de uma certa maneira, com base na entrada externa ou uso externo de entrada na consulta. As consultas [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] aceitam parâmetros em todas as partes onde literais são aceitos. Desenvolvedores de aplicativos devem usar consultas parametrizadas, em vez da o injetar literais de um agente externo diretamente na consulta.  
  
 Qualquer entrada direta ou indiretamente derivado de usuário ou um agente externa pode ter o conteúdo que aproveita a sintaxe de linguagem de destino para executar ações desautorizadas. Isso é conhecido como um ataque de injeção SQL, chamado depois que um padrão de ataque onde o idioma de destino é Transact-SQL. A entrada do usuário injetada diretamente na consulta é usada para soltar uma tabela de base de dados, causa uma negação de serviço, ou caso contrário alterar a natureza da operação que está sendo executada. Embora a composição de consulta é possível no [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], ela é realizada por meio da API do modelo de objeto. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]consultas não são compostas por meio de manipulação de cadeia de caracteres ou concatenação, como eles são no Transact-SQL e não são suscetíveis a ataques de injeção de SQL no sentido tradicional.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
