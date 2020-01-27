---
title: Modelos de transação
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: d6c78a5342bf19d19308352cddc241f436bfcb3a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745329"
---
# <a name="transaction-models"></a>Modelos de transação
Este tópico descreve a relação entre os modelos de programação de transação e os componentes de infraestrutura fornecidos pela Microsoft.  
  
 Ao usar transações no Windows Communication Foundation (WCF), é importante entender que você não está selecionando entre diferentes modelos transacionais, mas operando em camadas diferentes de um modelo integrado e consistente.  
  
 As seções a seguir descrevem os três componentes principais de transação.  
  
## <a name="windows-communication-foundation-transactions"></a>Transações de Windows Communication Foundation  
 O suporte a transações no WCF permite que você escreva serviços transacionais. Além disso, com seu suporte para o protocolo WS-AtomicTransaction (WS-AT), os aplicativos podem fluir transações para serviços Web criados usando o WCF ou tecnologia de terceiros.  
  
 Em um serviço ou aplicativo WCF, os recursos de transação do WCF fornecem atributos e configurações para especificar declarativamente como e quando a infraestrutura deve criar, fluir e sincronizar transações.  
  
## <a name="systemtransactions-transactions"></a>Transações de System. Transactions  
 O namespace <xref:System.Transactions> fornece um modelo de programação explícito baseado na classe <xref:System.Transactions.Transaction>, bem como um modelo de programação implícito usando a classe <xref:System.Transactions.TransactionScope>, na qual a infraestrutura gerencia automaticamente as transações.  
  
 Para obter mais informações sobre como criar um aplicativo transacional usando esses dois modelos, consulte [escrevendo um aplicativo transacional](https://go.microsoft.com/fwlink/?LinkId=94947).  
  
 Em um serviço ou aplicativo WCF, o <xref:System.Transactions> fornece o modelo de programação para criar transações em um aplicativo cliente e, para interagir explicitamente com uma transação, quando necessário, dentro de um serviço.  
  
## <a name="msdtc-transactions"></a>Transações MSDTC  
 O Microsoft Coordenador de Transações Distribuídas (MSDTC) é um Gerenciador de transações que fornece suporte para transações distribuídas.  
  
 Para obter mais informações, consulte a [referência do programador do DTC](https://docs.microsoft.com/previous-versions/windows/desktop/ms686108(v=vs.85)).  
  
 Em um serviço ou aplicativo WCF, o MSDTC fornece a infraestrutura para a coordenação de transações criadas dentro de um cliente ou serviço.
