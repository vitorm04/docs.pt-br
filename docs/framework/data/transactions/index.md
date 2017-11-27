---
title: "Processamento de transações"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5248dd3a4da450e411dd5d9a7843df6c9263026e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-processing"></a>Processamento de transações
Ao comprar um livro de livrarias online, você troca money (na forma de crédito) de um livro. Se o crédito é boa, uma série de operações relacionadas garante que você obtenha o livro e a livraria obtém seu dinheiro. No entanto, se uma única operação na série falhar durante a troca, toda a troca falhará. Você não obtiver o livro e a livraria não obter seu dinheiro.  
  
 A tecnologia responsável por fazer o intercâmbio equilibrado e previsível é chamada de processamento de transações. As transações garantem que recursos orientados a dados não são permanentemente atualizados, a menos que todas as operações dentro da unidade transacional foi concluída com êxito. Ao combinar um conjunto de operações relacionadas em uma unidade que completamente obtenha êxito ou falha completamente, você pode simplificar a recuperação de erro e tornar seu aplicativo mais confiável.  
  
 Sistemas de processamento de transação consistem em hardware e software que hospeda um aplicativo orientado a transações que executa as transações de rotina necessárias para conduzir os negócios. Os exemplos incluem sistemas de gerenciamento de entrada de ordem de venda, reservas de viagens, folha de pagamento, registros de funcionários, produção e a remessa.  
  
 Esta seção fornece informações gerais sobre o processamento de transações e informações específicas sobre como escrever aplicativos transacionais e gerenciadores de recursos usando o Microsoft .NET Framework.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Transaction Fundamentals](../../../../docs/framework/data/transactions/transaction-fundamentals.md) (Conceitos básicos de transação)  
 Apresenta os termos e conceitos de processamento de transações básicas.  
  
 [Features Provided by System.Transactions](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md) (Recursos fornecidos por System.Transactions)  
 Descreve como usar recursos do System. Transactions para escrever seu próprio aplicativo transacional.  
  
## <a name="reference"></a>Referência  
 <xref:System.Transactions>  
 Fornece classes que permitem que o seu código para participar de transações. As classes de suportam a transações com vários participantes distribuídos, várias notificações de fase e inscrições duráveis.
