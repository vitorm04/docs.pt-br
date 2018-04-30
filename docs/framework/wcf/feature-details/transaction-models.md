---
title: Modelos de transação
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3c68a23e9ee86050a9db4c63c8c97d017794bce8
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="transaction-models"></a>Modelos de transação
Este tópico descreve a relação entre os modelos de programação de transação e os componentes de infraestrutura, a Microsoft fornece.  
  
 Ao usar transações em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], é importante entender que você está não selecionando entre diferentes modelos transacionais, mas em vez disso, operando em diferentes camadas de um modelo consistente e integrada.  
  
 As seções a seguir descrevem os três componentes principais de transação.  
  
## <a name="windows-communication-foundation-transactions"></a>Transações do Windows Communication Foundation  
 O suporte a transações em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permite que você escrever serviços transacionais. Além disso, com o suporte para o protocolo WS-AtomicTransaction (WS-AT), aplicativos possam fluir transações de serviços da Web criados usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ou tecnologia de terceiros.  
  
 Em um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço ou aplicativo, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recursos de transação fornecem atributos e configuração para especificar declarativamente como e quando a infraestrutura deve criar, fluxo e sincronizar as transações.  
  
## <a name="systemtransactions-transactions"></a>Transações de System. Transactions  
 O <xref:System.Transactions> namespace fornece dois um modelo de programação explícito com base no <xref:System.Transactions.Transaction> classe, bem como um modelo de programação implícito usando a <xref:System.Transactions.TransactionScope> classe, em que a infraestrutura gerencia automaticamente as transações.  
  
 Para obter mais informações sobre como criar um aplicativo transacional usando esses dois modelos, consulte [escrevendo um aplicativo transacional](http://go.microsoft.com/fwlink/?LinkId=94947).  
  
 Em um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço ou aplicativo, <xref:System.Transactions> fornece o modelo de programação para criar transações dentro de um aplicativo cliente e explicitamente interagindo com uma transação, quando necessário, dentro de um serviço.  
  
## <a name="msdtc-transactions"></a>Transações do MSDTC  
 O Microsoft Distributed Transaction MSDTC (coordenador) é um Gerenciador de transações que fornece suporte para transações distribuídas.  
  
 Para obter mais informações, consulte o [referência do programador de DTC](http://go.microsoft.com/fwlink/?LinkId=94948).  
  
 Em um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço ou aplicativo, o MSDTC fornece a infraestrutura para a coordenação de transações criadas dentro de um cliente ou serviço.
