---
title: "Utilizando Transações WS-Atomic"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 12e6e2be3e01ea920b45cce7a27814dd19c00935
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="using-ws-atomictransaction"></a>Utilizando Transações WS-Atomic
WS-AtomicTransaction (WS-AT) é um protocolo de transação interoperável. Permite o fluxo de transações distribuídas por meio de mensagens do serviço Web e coordenar de maneira interoperável entre infraestruturas de transação heterogêneos. WS-AT usa o protocolo de confirmação de duas fases para direcionar um resultado atômico entre aplicativos distribuídos, gerenciadores de transações e os gerenciadores de recursos.  
  
 A implementação de WS-AT [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fornece inclui um serviço de protocolo incorporado ao Gerenciador de transações do coordenador de transações distribuídas da Microsoft (MSDTC). Usando o WS-AT [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos possam fluir transações para outros aplicativos, incluindo os serviços da Web interoperáveis construídos usando a tecnologia de terceiros.  
  
 Quando uma transação entre um aplicativo cliente e um aplicativo de servidor de fluxo, o protocolo de transação usado é determinado pela associação que o servidor expõe no ponto de extremidade de cliente selecionado. Alguns [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] padrão de associações fornecidas pelo sistema para especificar o `OleTransactions` protocolo como o formato de propagação de transação, enquanto outros padrão à especificação WS-AT. Você pode modificar também programaticamente a opção de protocolo de transação dentro de uma associação fornecida.  
  
 A escolha de protocol influencia:  
  
-   O formato dos cabeçalhos de mensagem usado para a transação do cliente ao servidor de fluxo.  
  
-   O protocolo de rede usado para executar o protocolo de confirmação de duas fases entre o Gerenciador de transações do cliente e da transação do servidor, para resolver o resultado da transação.  
  
 Se o cliente e servidor são escritos usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], você não precisa usar WS-AT. Em vez disso, você pode usar as configurações padrão de `NetTcpBinding` com o `TransactionFlow` atributo habilitado, que usará o `OleTransactions` protocolo em vez disso. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md). Caso contrário, se o fluxo de transações para serviços da Web criados nas tecnologias de terceiros, você deve usar WS-AT.  
  
## <a name="see-also"></a>Consulte também  
 [Configurando o suporte a transações WS-Atomic](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
