---
title: Transações e simultaneidade
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: 049e402345e1abbb46739e48c89101207a43bb27
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191665"
---
# <a name="transactions-and-concurrency"></a>Transações e simultaneidade

Uma transação consiste em um único comando ou em um grupo de comandos executados como um pacote. As transações permitem que você combine várias operações em uma única unidade de trabalho. Se uma falha ocorrer em determinado ponto na transação, todas as atualizações poderão ser revertidas para o estado em vigor antes da transação.  
  
 Uma transação deve estar de acordo com as propriedade ACID — atomicidade, consistência, isolamento e durabilidade — para garantir a consistência dos dados. A maioria dos sistemas de banco de dados relacional, como o Microsoft SQL Server, oferece suporte a transações fornecendo recursos de bloqueio, registro e gerenciamento de transação sempre que um aplicativo cliente executa uma operação de atualização, inserção ou exclusão.  
  
> [!NOTE]
> As transações que envolvem vários recursos podem reduzir a simultaneidade se os bloqueios forem mantidos muito longos. Portanto, mantenha as transações curtas, o quanto possível.  
  
 Se uma transação envolver várias tabelas no mesmo banco de dados ou servidor, as transações explícitas em procedimentos armazenados geralmente apresentarão um melhor desempenho. Você pode criar transações em procedimentos armazenados do SQL Server usando as instruções Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION` e `ROLLBACK TRANSACTION`. Para obter mais informações, consulte os Manuais Online do SQL Server.  
  
 As transações que envolvem diferentes gerenciadores de recursos, como uma transação entre SQL Server e Oracle, exigem uma transação distribuída.  
  
## <a name="in-this-section"></a>Nesta seção  

 [Transações locais](local-transactions.md)  
 Demonstra como executar transações em um banco de dados.  
  
 [Transações distribuídas](distributed-transactions.md)  
 Descreve como executar transações distribuídas no ADO.NET.  
  
 [Integração de System.Transactions com o SQL Server](system-transactions-integration-with-sql-server.md)  
 Descreve <xref:System.Transactions> a integração com o SQL Server para trabalhar com transações distribuídas.  
  
 [Simultaneidade otimista](optimistic-concurrency.md)  
 Descreve a simultaneidade otimista e pessimista, e como você pode testar as violações de simultaneidade.  
  
## <a name="see-also"></a>Veja também

- [Conceitos básicos de transação](../transactions/transaction-fundamentals.md)
- [Conectando a uma Fonte de Dados](connecting-to-a-data-source.md)
- [Comandos e parâmetros](commands-and-parameters.md)
- [DataAdapters e DataReaders](dataadapters-and-datareaders.md)
- [DbProviderFactories](dbproviderfactories.md)
- [Visão geral do ADO.NET](ado-net-overview.md)
