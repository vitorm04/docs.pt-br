---
title: Snap-in do MMC de configuração de WS-AtomicTransaction
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e8b127e0d3c241a1e37ac2161d9fadcea990425
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a>Snap-in do MMC de configuração de WS-AtomicTransaction
O Snap-in MMC de configuração de WS-AtomicTransaction é usado para configurar uma parte das configurações do WS-AtomicTransaction em computadores locais e remotos.  
  
## <a name="remarks"></a>Comentários  
 Se você estiver executando [!INCLUDE[wxp](../../../includes/wxp-md.md)] ou [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], o snap-in do MMC pode ser encontrado navegando para **controle administrativo/painel de ferramentas/serviços de componentes /**, com o botão direito **meu computador**, e selecionando **propriedades**. Este é o mesmo local onde você pode configurar o MSDTC. Opções disponíveis para configuração são agrupadas sob o **WS-AT** guia.  
  
 Se você estiver executando o Windows Vista ou [!INCLUDE[lserver](../../../includes/lserver-md.md)], snap-in do MMC pode ser encontrado clicando o **iniciar** botão e digitando `dcomcnfg.exe` no **pesquisa** caixa. Quando o MMC é aberto, navegue até o **Meus Computer\Distributed transação Coordinator\Local DTC** nó, clique com botão direito e selecione **propriedades**. Opções disponíveis para configuração são agrupadas sob o **WS-AT** guia.  
  
 As etapas anteriores são usadas para iniciar o snap-in para configurar um computador local. Se você quiser configurar um computador remoto, você deve localizar o nome da máquina remota em **controle administrativo/painel de ferramentas/serviços de componentes /** e realizar etapas semelhantes, se você estiver executando [!INCLUDE[wxp](../../../includes/wxp-md.md)] ou [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Se você estiver executando o Windows Vista ou [!INCLUDE[lserver](../../../includes/lserver-md.md)], siga as etapas anteriores para Vista e [!INCLUDE[lserver](../../../includes/lserver-md.md)], mas usar o **Coordinator\Local de transações distribuídas DTC** nó no nó do computador remoto.  
  
 Para usar a interface de usuário fornecida pela ferramenta, você precisa registrar o arquivo WsatUI.dll, que está localizado no seguinte caminho,  
  
 **%ProgramFiles%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**  
  
 O registro pode ser feito pelo comando a seguir.  
  
```Output  
regasm.exe /codebase WsatUI.dll  
```  
  
 Você pode usar essa ferramenta para modificar as configurações básicas do WS-AtomicTransaction. Por exemplo, você pode habilitar e desabilitar o suporte de protocolo WS-AtomicTransaction, configurar as portas HTTP para WS-AT, associar um certificado SSL à porta HTTP, configurar certificados especificando nomes de entidade do certificado, selecione o modo de rastreamento e definir tempo limite padrão e máximo.  
  
 Se você deve configurar o suporte do WS-AtomicTransaction no computador local, você pode usar a versão de linha de comando da ferramenta. Para obter mais informações sobre a ferramenta de linha de comando, consulte o [o utilitário de configuração do WS-AtomicTransaction (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md) tópico.  
  
 Você deve estar ciente de que tanto o Snap-in do MMC e a ferramenta de linha de comando não oferecem suporte à configuração todas as configurações de WS-AT. Essas configurações podem ser editadas somente modificando o registro diretamente. Para obter mais informações sobre essas configurações do registro, consulte [configurando suporte a transações WS-Atomic](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
### <a name="user-interface-description"></a>Descrição de Interface do usuário  
 **Habilitar o suporte de rede WS-AT**:  
  
 Alternar essa caixa de seleção habilita ou desabilita todos os componentes de GUI do snap-in.  
  
 Antes de marcar esta caixa, você deve garantir que o acesso DTC de rede está habilitado com a comunicação de entrada ou saída, ou ambos. Esse valor pode ser verificado no **segurança** guia do snap-in do MSDTC.  
  
#### <a name="network-group-box"></a>Caixa de grupo de rede  
 Você pode especificar a porta HTTPS e configurações de segurança adicionais, como a criptografia SSL no grupo de rede. Esse grupo é desabilitado (esmaecido) se as transações de rede do DTC não estiverem habilitadas.  
  
 **Porta HTTPS**  
  
 Esse é o valor da porta HTTPS usada para WS-AT. O valor deve ser um número no intervalo de 1 a 65535 (represente uma porta válida). Alterar a porta HTTP modifica a configuração de serviço HTTP, o que significa que o endereço do serviço WS-AT usadas anteriormente é liberado e um novo endereço de serviço WS-AT está registrado com base na nova porta. Além disso, a porta selecionada recentemente é criptografada com o certificado selecionado atualmente para a criptografia SSL.  
  
> [!NOTE]
>  Se você já tiver ativado o firewall antes de executar essa ferramenta, a porta será registrada automaticamente na lista de exceções. Se o firewall está desabilitado antes de executar essa ferramenta, nenhuma tarefa adicional é configurada sobre o firewall.  
  
 Se você habilitar o firewall após a configuração WS-AT, você deve executar essa ferramenta novamente e forneça o número de porta que o uso desse parâmetro. Se você desabilitar o firewall depois de configurar, WS-AT continuará a funcionar sem entrada adicional.  
  
 **Certificado de ponto de extremidade**  
  
 Clique o **selecione** botão exibe uma lista com os certificados disponíveis no momento no computador Local, permitindo que o usuário selecionar o certificado que pode ser usado para criptografia SSL. Os certificados devem ter uma chave privada. Caso contrário, você receberá uma mensagem de erro.  
  
> [!NOTE]
>  Quando você definir um certificado SSL para uma porta selecionada, você substituir o certificado SSL original associado a essa porta se houver.  
  
 **Contas autorizadas**  
  
 Clicando o **selecione** botão invoca o editor de lista de controle de acesso do Windows, onde você pode especificar o usuário ou grupo que pode participar de transações de WS-Atomic verificando o **permitir** ou **Deny** caixa o **participar** grupo de permissão.  
  
 **Certificados autorizados**  
  
 Clique o **selecione** botão exibe uma lista de certificados disponíveis no momento em LocalMachine. Você pode selecionar quais identidades de certificado podem participar de transações de WS-Atomic.  
  
#### <a name="timeout-group-box"></a>Caixa de grupo de tempo limite  
 O **tempo limite** caixa de grupo permite que você especifique o tempo limite padrão e máximo para uma transação WS-Atomic. Um valor válido para o tempo limite de saída está entre 1 e 3600. Um valor válido para o tempo limite de entrada está entre 0 e 3600.  
  
#### <a name="tracing-and-logging-group-box"></a>Rastreamento e registro de caixa de grupo  
 O **de rastreamento e registro** caixa de grupo permite que você configure o nível de log e rastreamento desejado.  
  
 Clique o **opções** botão invoca uma página onde você pode especificar configurações adicionais.  
  
 O **nível de rastreamento** caixa de combinação permite que você escolha de qualquer valor válido do <xref:System.Diagnostics.TraceLevel> enumeração. Você também pode usar as caixas de seleção para especificar se deseja executar o rastreamento de atividade, propagação de atividade ou coletar informações de identificação pessoal.  
  
 Você também pode especificar as sessões de log no **log de sessão** caixa de grupo.  
  
> [!NOTE]
>  Quando usar o provedor de rastreamento do WS-AT outro consumidor de rastreamento, você não pode criar uma nova sessão de log de eventos de rastreamento. Qualquer tentativa de configurar o log durante esse tempo resulta na mensagem de erro "Falha ao ativar provedor. Código de erro: 1".  
  
 Para obter mais informações sobre o rastreamento e registro em log, consulte [administração e diagnósticos](../../../docs/framework/wcf/diagnostics/index.md).  
  
## <a name="see-also"></a>Consulte também  
 [Configurando o suporte a transações WS-Atomic](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)  
 [Utilitário de configuração de WS-AtomicTransaction (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)  
 [Administração e diagnósticos](../../../docs/framework/wcf/diagnostics/index.md)
