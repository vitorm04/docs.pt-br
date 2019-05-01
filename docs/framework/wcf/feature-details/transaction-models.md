---
title: Modelos de transação
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 8731b72d0657aa420dbb020e216c3af059916ce9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050773"
---
# <a name="transaction-models"></a>Modelos de transação
Este tópico descreve a relação entre os modelos de programação de transação e a Microsoft fornece os componentes da infraestrutura.  
  
 Ao usar transações no Windows Communication Foundation (WCF), é importante entender que você estiver não selecionando entre diferentes modelos transacionais, mas em vez disso, operando em diferentes camadas de um modelo consistente e integrado.  
  
 As seções a seguir descrevem os três componentes de transação principal.  
  
## <a name="windows-communication-foundation-transactions"></a>Transações do Windows Communication Foundation  
 O suporte a transações no WCF permite que você escrever serviços transacionais. Além disso, com seu suporte para o protocolo WS-AtomicTransaction (WS-AT), aplicativos podem fluir transações a serviços Web criados usando o WCF ou tecnologia de produtos de terceiros.  
  
 Em um aplicativo ou serviço do WCF, recursos de transação do WCF fornecem atributos e a configuração para especificar declarativamente como e quando a infraestrutura deve criar, fluxo e sincronizar as transações.  
  
## <a name="systemtransactions-transactions"></a>Transações de System. Transactions  
 O <xref:System.Transactions> namespace fornece dois um modelo de programação explícito com base em de <xref:System.Transactions.Transaction> classe, bem como um modelo de programação implícito usando a <xref:System.Transactions.TransactionScope> classe, em que a infra-estrutura gerencia automaticamente as transações.  
  
 Para obter mais informações sobre como criar um aplicativo transacional usando esses dois modelos, consulte [escrevendo um aplicativo transacional](https://go.microsoft.com/fwlink/?LinkId=94947).  
  
 Em um aplicativo, ou um serviço WCF <xref:System.Transactions> fornece o modelo de programação para criação de transações em um aplicativo cliente e explicitamente interagindo com uma transação, quando necessário, dentro de um serviço.  
  
## <a name="msdtc-transactions"></a>Transações do MSDTC  
 O Microsoft Distributed Transaction Coordinator (MSDTC) é um Gerenciador de transações que fornece suporte para transações distribuídas.  
  
 Para obter mais informações, consulte o [referência do programador de DTC](https://go.microsoft.com/fwlink/?LinkId=94948).  
  
 Em um aplicativo ou serviço do WCF, o MSDTC fornece a infraestrutura para a coordenação de transações criadas dentro de um cliente ou serviço.
