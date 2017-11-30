---
title: "Escalonamento de bloqueios de gerenciamento de transação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e96331e-31b6-4272-bbbd-29ed1e110460
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0ac45390d78f4fbce15c8910fcdcc95713c5898a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-management-escalation"></a>Escalonamento de bloqueios de gerenciamento de transação
Windows hospeda um conjunto de serviços e módulos que constituem uma transação manager. Escalonamento de gerenciamento de transações descreve o processo de migração de uma transação de um dos componentes do Gerenciador de transações para outro.  
  
 <xref:System.Transactions>inclui um componente do Gerenciador de transações que coordena uma transação envolvendo no máximo, um único recurso durável ou vários recursos voláteis. Como o Gerenciador de transações usa apenas chamadas de domínio intra-aplicativo, ele gera o melhor desempenho. Os desenvolvedores não precisam interagir diretamente com o Gerenciador de transações. Em vez disso, uma infra-estrutura comum que define o comportamento comum, interfaces e classes auxiliares é fornecida pelo <xref:System.Transactions> namespace.  
  
 Quando você deseja fornecer a transação a um objeto em outro domínio de aplicativo (incluindo entre limites de processo e de máquina) no mesmo computador, o <xref:System.Transactions> infraestrutura aumenta automaticamente a transação a ser gerenciado pelo Microsoft Coordenador de transações distribuídas (MSDTC). O escalonamento também ocorrerá se você inscrever outro gerenciador de recursos duráveis. Quando escalonado, a transação permanecerá gerenciada em seu estado com privilégios elevados até sua conclusão.  
  
 Entre os <xref:System.Transactions> transação e transação MSDTC, existe um tipo de intermediário da transação que é disponibilizado por meio de inscrição de fase única (PSPE) podem ser promovidas. PSPE é outro mecanismo importante em <xref:System.Transactions> para otimizar o desempenho. Ele permite que um recurso durável remoto localizado em um domínio de aplicativo diferente, o processo ou o computador participe de um <xref:System.Transactions> transação sem fazer com que ele ser escalonado para uma transação MSDTC. Para obter mais informações sobre PSPE, consulte [inscrição recursos como participantes em uma transação](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md).  
  
## <a name="how-escalation-is-initiated"></a>Como o escalonamento de bloqueios é iniciado  
 Escalonamento de bloqueios de transação reduz o desempenho porque o MSDTC reside em um processo separado e escalonar uma transação ao MSDTC resulta em mensagens sendo enviadas em processo. Para melhorar o desempenho, você deve atrasar ou evitar o escalonamento de bloqueios para MSDTC; Portanto, você precisa saber como e quando o escalonamento é iniciado.  
  
 Como o <xref:System.Transactions> infra-estrutura trata recursos voláteis e no máximo uma durável de recurso que dá suporte a notificações de fase única, a transação permanece na propriedade do <xref:System.Transactions> infra-estrutura. O Gerenciador de transações avails em si, apenas a esses recursos que ao vivo no mesmo domínio do aplicativo e para o qual o log (gravar o resultado da transação no disco) não é necessário. Um escalonamento resulta no <xref:System.Transactions> infra-estrutura, transferindo a propriedade da transação ao MSDTC acontece quando:  
  
-   Pelo menos um recurso durável que não dá suporte a notificações de fase única é inscrita na transação.  
  
-   Pelo menos dois recursos duráveis que oferecem suporte a notificações de fase única estão inscritos na transação. Por exemplo, a inscrição de uma única conexão com [!INCLUDE[sqprsqlong](../../../../includes/sqprsqlong-md.md)] não faz com que uma transação seja promovido. No entanto, sempre que você abrir uma segunda conexão com um [!INCLUDE[sqprsqlong](../../../../includes/sqprsqlong-md.md)] banco de dados fazendo com que o banco de dados para se inscrever, o <xref:System.Transactions> infra-estrutura detecta que ele é o segundo recurso durável na transação e escala para uma transação MSDTC.  
  
-   Uma solicitação de "empacotar" a transação para um domínio de aplicativo diferente ou outro processo é chamada. Por exemplo, a serialização do objeto de transação em um limite de domínio de aplicativo. O objeto de transação é empacotado por valor, que significa que qualquer tentativa de passá-lo em um limite de domínio de aplicativo (e até mesmo no mesmo processo) resulta na serialização do objeto de transação. Você pode passar os objetos de transação, fazendo uma chamada em um método remoto que usa um <xref:System.Transactions.Transaction> como um parâmetro ou você pode tentar acessar um componente remoto transacional é atendido. Isso serializa o objeto de transação e resulta em um escalonamento, como quando uma transação é serializada em um domínio de aplicativo. Ele é distribuído e o Gerenciador de transações local não é mais adequado.  
  
 A tabela a seguir lista todas as exceções possíveis que podem ser geradas durante a expansão.  
  
|Tipo de Exceção|Condição|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Uma tentativa para escalonar uma transação com o nível de isolamento igual a <xref:System.Transactions.IsolationLevel.Snapshot>.|  
|<xref:System.Transactions.TransactionAbortedException>|O Gerenciador de transações está inativo.|  
|<xref:System.Transactions.TransactionException>|O escalonamento de bloqueios falha e o aplicativo será anulado.|
