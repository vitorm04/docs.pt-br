---
title: Transações e simultaneidade
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: ba857031a54374ee295c2bfd724e7fb8651b7c1f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174688"
---
# <a name="transactions-and-concurrency"></a>Transações e simultaneidade
Uma transação consiste em um único comando ou em um grupo de comandos executados como um pacote. As transações permitem que você combine várias operações em uma única unidade de trabalho. Se uma falha ocorrer em determinado ponto na transação, todas as atualizações poderão ser revertidas para o estado em vigor antes da transação.  
  
 Uma transação deve estar de acordo com as propriedade ACID — atomicidade, consistência, isolamento e durabilidade — para garantir a consistência dos dados. A maioria dos sistemas de banco de dados relacional, como o Microsoft SQL Server, oferece suporte a transações fornecendo recursos de bloqueio, registro e gerenciamento de transação sempre que um aplicativo cliente executa uma operação de atualização, inserção ou exclusão.  
  
> [!NOTE]
>  As transações que envolvem vários recursos podem reduzir a simultaneidade se os bloqueios forem mantidos muito longos. Portanto, mantenha as transações curtas, o quanto possível.  
  
 Se uma transação envolver várias tabelas no mesmo banco de dados ou servidor, as transações explícitas em procedimentos armazenados geralmente apresentarão um melhor desempenho. Você pode criar transações em procedimentos armazenados do SQL Server usando as instruções Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION` e `ROLLBACK TRANSACTION`. Para obter mais informações, consulte os Manuais Online do SQL Server.  
  
 Transações que envolvem diferentes gerentes de recursos, como uma transação entre o SQL Server e Oracle, requerem uma transação distribuída.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Transações locais](../../../../docs/framework/data/adonet/local-transactions.md)  
 Demonstra como executar transações em um banco de dados.  
  
 [Transações distribuídas](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 Descreve como executar transações distribuídas no ADO.NET.  
  
 [Integração de System.Transactions com o SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 Descreve <xref:System.Transactions> transações distribuídas de integração com o SQL Server para trabalhar com.  
  
 [Simultaneidade otimista](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 Descreve a simultaneidade otimista e pessimista, e como você pode testar as violações de simultaneidade.  
  
## <a name="see-also"></a>Consulte também

- [Transaction Fundamentals](../../../../docs/framework/data/transactions/transaction-fundamentals.md) (Conceitos básicos de transação)
- [Conectando a uma fonte de dados](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [Comandos e parâmetros](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [DataAdapters e DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
