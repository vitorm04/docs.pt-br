---
title: Snap-in do MMC de configuração de WS-AtomicTransaction
ms.date: 03/30/2017
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
ms.openlocfilehash: b1d86fa57b31d1f9be12f76c28f9d042e7e28e24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052554"
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a>Snap-in do MMC de configuração de WS-AtomicTransaction
O Snap-in do MMC de configuração WS-AtomicTransaction é usado para configurar uma parte das configurações WS-AtomicTransaction nos computadores locais e remoto.  
  
## <a name="remarks"></a>Comentários  
 Se você estiver executando [!INCLUDE[wxp](../../../includes/wxp-md.md)] ou [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], o snap-in do MMC pode ser encontrado navegando para **serviços de controle de painel/Administrative ferramentas/componentes /**, com o botão direito **meu computador**, e selecionando **propriedades**. Isso é o mesmo local onde você pode configurar o MSDTC. As opções disponíveis para configuração estão agrupadas sob o **WS-AT** guia.  
  
 Se você estiver executando o Windows Vista ou [!INCLUDE[lserver](../../../includes/lserver-md.md)], snap-in do MMC pode ser encontrado clicando o **começar** botão e digitando `dcomcnfg.exe` no **pesquisa** caixa. Quando o MMC for aberto, navegue até a **Meus Computer\Distributed transação Coordinator\Local DTC** nó, clique com botão direito e selecione **propriedades**. As opções disponíveis para configuração estão agrupadas sob o **WS-AT** guia.  
  
 As etapas anteriores são usadas para iniciar o snap-in para configurar um computador local. Se você quiser configurar um computador remoto, você deve localizar o nome do computador remoto no **serviços de controle de painel/Administrative ferramentas/componentes /** e executar etapas semelhantes se você estiver executando [!INCLUDE[wxp](../../../includes/wxp-md.md)] ou [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Se você estiver executando o Windows Vista ou [!INCLUDE[lserver](../../../includes/lserver-md.md)], siga as etapas anteriores para o Vista e [!INCLUDE[lserver](../../../includes/lserver-md.md)], mas usar o **Coordinator\Local de transações distribuídas DTC** nó sob o nó do computador remoto.  
  
 Para usar a interface do usuário fornecida pela ferramenta, você deve registrar o arquivo WsatUI.dll, que está localizado no seguinte caminho,  
  
 **%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**  
  
 O registro pode ser feito pelo comando a seguir.  
  
```Output  
regasm.exe /codebase WsatUI.dll  
```  
  
 Você pode usar essa ferramenta para modificar as configurações básicas de WS-AtomicTransaction. Por exemplo, você pode habilitar e desabilitar o suporte de protocolo WS-AtomicTransaction, configurar as portas HTTP para WS-AT, associar um certificado SSL à porta HTTP, configurar certificados com a especificação de nomes de entidade do certificado, selecione o modo de rastreamento e definir tempos limite máximo e padrão.  
  
 Se você precisa configurar o suporte de WS-AtomicTransaction no computador local, você pode usar a versão de linha de comando dessa ferramenta. Para obter mais informações sobre a ferramenta de linha de comando, consulte o [WS-AtomicTransaction utilitário de configuração (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md) tópico.  
  
 Você deve estar ciente de que tanto o Snap-in do MMC e a ferramenta de linha de comando não dão suporte a configuração de todas as configurações de WS-AT. Essas configurações podem ser editadas apenas ao modificar o registro diretamente. Para obter mais informações sobre essas configurações do registro, consulte [Configurando o suporte a transações WS-Atomic](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
### <a name="user-interface-description"></a>Descrição da Interface do usuário  
 **Habilitar o suporte a transações WS-Atomic rede**:  
  
 Ativar/desativar esta caixa de seleção habilita ou desabilita todos os componentes de GUI do snap-in.  
  
 Antes de marcar esta caixa, assegure-se de que o acesso DTC de rede está habilitado com a comunicação de entrada ou saída, ou ambos. Esse valor pode ser verificado na **segurança** guia do snap-in do MSDTC.  
  
#### <a name="network-group-box"></a>Caixa de grupo de rede  
 Você pode especificar a porta HTTPS e configurações de segurança adicionais, como a criptografia SSL, no grupo de rede. Este grupo está desabilitado (esmaecido) se as transações de rede do DTC não estiverem habilitadas.  
  
 **Porta HTTPS**  
  
 Esse é o valor da porta HTTPS usada para WS-AT. O valor deve ser um número no intervalo de 1 a 65535 (como para representar uma porta válida). Alterar a porta HTTP modifica a configuração de serviço HTTP, o que significa que o endereço de serviço usadas anteriormente WS-AT é liberado e um novo endereço de serviço WS-AT está registrado com base na nova porta. Além disso, a porta recém-selecionado é criptografada com o certificado selecionado no momento para criptografia SSL.  
  
> [!NOTE]
>  Se você já tiver habilitado o firewall antes de executar essa ferramenta, a porta é registrada automaticamente na lista de exceções. Se o firewall está desabilitado antes de executar essa ferramenta, nada mais é configurado sobre o firewall.  
  
 Se você habilitar o firewall depois de configurar WS-AT, você deve executar essa ferramenta novamente e forneça o número de porta que o uso desse parâmetro. Se você desabilitar o firewall depois de configurar, WS-AT continua a funcionar sem entrada adicional.  
  
 **Certificado de ponto de extremidade**  
  
 Clicar a **selecionar** botão exibe uma lista com os certificados disponíveis atualmente no computador Local, permitindo que o usuário selecione o certificado que pode ser usado para criptografia SSL. Os certificados devem ter uma chave privada. Caso contrário, você receberá uma mensagem de erro.  
  
> [!NOTE]
>  Quando você definir um certificado SSL para uma porta selecionada, você pode substituir o certificado SSL original associado com essa porta, se houver um.  
  
 **Contas autorizadas**  
  
 Clicar na **selecionar** botão invoca o editor de lista de controle de acesso do Windows, onde você pode especificar o usuário ou grupo que pode participar em transações WS-Atomic verificando o **permitir** ou **Deny** caixa de **participar** grupo de permissão.  
  
 **Autorizované Certifikáty**  
  
 Clicar a **selecionar** botão exibe uma lista de certificados disponíveis atualmente no LocalMachine. Em seguida, você pode selecionar quais identidades de certificado têm permissão para participar de transações WS-Atomic.  
  
#### <a name="timeout-group-box"></a>Caixa de grupo de tempo limite  
 O **Timeout** caixa de grupo permite que você especifique o tempo limite máximo e padrão para uma transação de WS-Atomic. Um valor válido para o tempo limite de saída está entre 1 e 3600. Um valor válido para o tempo limite de entrada está entre 0 e 3600.  
  
#### <a name="tracing-and-logging-group-box"></a>Rastreamento e registro da caixa de grupo  
 O **rastreamento e registro** caixa de grupo permite que você configure o nível de registro em log e rastreamento desejado.  
  
 Clicar a **opções** botão invoca uma página onde você pode especificar configurações adicionais.  
  
 O **nível de rastreamento** caixa de combinação permite que você escolha de qualquer valor válido do <xref:System.Diagnostics.TraceLevel> enumeração. Você também pode usar as caixas de seleção para especificar se deseja executar o rastreamento de atividade, propagação de atividade ou coletar informações de identificação pessoal.  
  
 Você também pode especificar as sessões de registro em log na **sessão de registro em log** caixa de grupo.  
  
> [!NOTE]
>  Quando outro consumidor de rastreamento estiver usando o provedor de rastreamento WS-AT, é possível criar uma nova sessão de registro em log para eventos de rastreamento. Qualquer tentativa de configurar o registro em log durante esse tempo resulta na mensagem de erro "Falha ao habilitar provedor. Código de erro: 1".  
  
 Para obter mais informações sobre o rastreamento e registro em log, consulte [administração e diagnósticos](../../../docs/framework/wcf/diagnostics/index.md).  
  
## <a name="see-also"></a>Consulte também

- [Configurando o suporte a transações WS-Atomic](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
- [Utilitário de configuração de WS-AtomicTransaction (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [Administração e diagnósticos](../../../docs/framework/wcf/diagnostics/index.md)
