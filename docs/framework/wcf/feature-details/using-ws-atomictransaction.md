---
title: Utilizando Transações WS-Atomic
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
ms.openlocfilehash: 8a8265873e4287e1455659aa4d9fae7e1d570a00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932841"
---
# <a name="using-ws-atomictransaction"></a>Utilizando Transações WS-Atomic
WS-AtomicTransaction (WS-AT) é um protocolo de transação interoperável. Ele permite que você fluxo de transações distribuídas por meio de mensagens do serviço Web e coordenar de maneira interoperável entre infraestruturas de transação heterogêneos. WS-AT usa o protocolo de confirmação de duas fases para orientar um resultado atômico entre aplicativos distribuídos, gerenciadores de transações e gerenciadores de recursos.  
  
 A implementação de WS-AT fornece Windows Communication Foundation (WCF) inclui um serviço de protocolo integrado ao Gerenciador de transações Microsoft Distributed Transaction coordenador (MSDTC). Usando WS-AT, os aplicativos do WCF podem fluir transações para outros aplicativos, incluindo serviços da Web interoperáveis construídos usando a tecnologia de produtos de terceiros.  
  
 Quando uma transação entre um aplicativo cliente e um aplicativo de servidor de fluxo, o protocolo de transação usado é determinado pela associação que o servidor expõe no ponto de extremidade do cliente selecionado. Algum padrão de associações fornecidas pelo sistema do WCF para especificar o `OleTransactions` protocolo como o formato de propagação de transação, enquanto outras pessoas o padrão especificando WS-AT. Você pode modificar também programaticamente a opção de protocolo de transação dentro de uma determinada vinculação.  
  
 A escolha de protocolo influências:  
  
- O formato dos cabeçalhos de mensagem usado para fluir a transação do cliente ao servidor.  
  
- O protocolo de rede usado para executar o protocolo de confirmação de duas fases entre o Gerenciador de transações do cliente e da transação do servidor, para resolver o resultado da transação.  
  
 Se o servidor e cliente são escritos usando o WCF, você não precisará usar WS-AT. Em vez disso, você pode usar as configurações padrão de `NetTcpBinding` com o `TransactionFlow` atributo habilitado, que usará o `OleTransactions` de protocolo em vez disso. Para obter mais informações, consulte [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md). Caso contrário, se você estiver fluindo transações a serviços Web criados com as tecnologias de terceiros, você deve usar WS-AT.  
  
## <a name="see-also"></a>Consulte também

- [Configurando o suporte a transações WS-Atomic](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
