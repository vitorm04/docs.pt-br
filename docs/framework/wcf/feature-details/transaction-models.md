---
title: Modelos de transação
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 9efe8c6994cc80957b707bbae0885a3c5896f70a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="transaction-models"></a>Modelos de transação
Este tópico descreve a relação entre os modelos de programação de transação e os componentes de infraestrutura, a Microsoft fornece.  
  
 Ao usar transações no Windows Communication Foundation (WCF), é importante entender que você está não selecionando entre diferentes modelos transacionais, mas em vez disso, operando em diferentes camadas de um modelo consistente e integrada.  
  
 As seções a seguir descrevem os três componentes principais de transação.  
  
## <a name="windows-communication-foundation-transactions"></a>Transações do Windows Communication Foundation  
 O suporte de transação do WCF permite que você escrever serviços transacionais. Além disso, com o suporte para o protocolo WS-AtomicTransaction (WS-AT), aplicativos possam fluir transações de serviços da Web criados usando o WCF ou tecnologia de terceiros.  
  
 Em um aplicativo ou serviço WCF, recursos de transação do WCF fornecem atributos e configuração para especificar declarativamente como e quando a infraestrutura deve criar, fluxo e sincronizar as transações.  
  
## <a name="systemtransactions-transactions"></a>Transações de System. Transactions  
 O <xref:System.Transactions> namespace fornece dois um modelo de programação explícito com base no <xref:System.Transactions.Transaction> classe, bem como um modelo de programação implícito usando a <xref:System.Transactions.TransactionScope> classe, em que a infraestrutura gerencia automaticamente as transações.  
  
 Para obter mais informações sobre como criar um aplicativo transacional usando esses dois modelos, consulte [escrevendo um aplicativo transacional](http://go.microsoft.com/fwlink/?LinkId=94947).  
  
 Em um aplicativo, ou um serviço WCF <xref:System.Transactions> fornece o modelo de programação para criar transações dentro de um aplicativo cliente e explicitamente interagindo com uma transação, quando necessário, dentro de um serviço.  
  
## <a name="msdtc-transactions"></a>Transações do MSDTC  
 O Microsoft Distributed Transaction MSDTC (coordenador) é um Gerenciador de transações que fornece suporte para transações distribuídas.  
  
 Para obter mais informações, consulte o [referência do programador de DTC](http://go.microsoft.com/fwlink/?LinkId=94948).  
  
 Em um aplicativo ou serviço WCF, o MSDTC fornece a infraestrutura para a coordenação de transações criadas dentro de um cliente ou serviço.
