---
title: Utilitário de configuração de transações WS-Atomic (wsatConfig.exe)
ms.date: 03/30/2017
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
ms.openlocfilehash: 224777fe5bf8e8d832ede582f460a8fa6ae6181d
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802339"
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>Utilitário de configuração de transações WS-Atomic (wsatConfig.exe)
O utilitário de configuração WS-AtomicTransaction é usado para definir configurações básicas de suporte WS-AtomicTransaction.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Comentários  
 Essa ferramenta de linha de comando pode ser usada para definir configurações básicas do WS-AT somente em um computador local. Se você tiver que definir as configurações em máquinas locais e remotas, deverá usar o snap-in do MMC, conforme descrito em [Configurando o suporte à transação WS-Atomic](./feature-details/configuring-ws-atomic-transaction-support.md).  
  
 A ferramenta de linha de comando pode ser encontrada no local de instalação do SDK do Windows, especificamente,  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\wsatConfig.exe  
  
 Se você estiver executando [!INCLUDE[wxp](../../../includes/wxp-md.md)] ou [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], deverá baixar uma atualização antes de executar o WsatConfig. exe. Para obter mais informações sobre essa atualização, consulte [Update for Windows Communication Foundation (KB912817)](https://www.microsoft.com/en-us/download/details.aspx?id=21520).  
  
 A tabela a seguir mostra as opções que podem ser usadas com o utilitário de configuração WS-AtomicTransaction (wsatConfig. exe).  
  
> [!NOTE]
> Ao definir um certificado SSL para uma porta selecionada, você substitui o certificado SSL original associado a essa porta, se houver.  
  
|Opções|Descrição|  
|-------------|-----------------|  
|-contas: conta de\<, >|Especifica uma lista separada por vírgulas de contas que podem participar de WS-AtomicTransaction. A validade dessas contas não está marcada.|  
|-accountsCerts:\<thumb>&#124;"Issuer\SubjectName",>|Especifica uma lista separada por vírgulas de certificados que podem participar de WS-AtomicTransaction. Os certificados são indicados por impressão digital ou pelo par Issuer\SubjectName. Use {EMPTY} para o nome da entidade se ele estiver vazio.|  
|-endpointCert: < Machine&#124;\<Thumb >&#124;"Issuer\SubjectName" >|Usa o certificado do computador ou outro certificado de ponto de extremidade local especificado por um par de impressão digital ou Issuer\SubjectName. Usa {EMPTY} para o nome da entidade se ele estiver vazio.|  
|-maxTimeout:\<s >|Especifica o tempo limite máximo em segundos. Os valores válidos são de 0 a 3600.|  
|-Network:\<habilitar&#124;desabilitar >|Habilita ou desabilita o suporte de rede WS-AtomicTransaction.|  
|-Port:\<portNum >|Define a porta HTTPS para WS-AtomicTransaction.<br /><br /> Se você já tiver habilitado o firewall antes de executar essa ferramenta, a porta será automaticamente registrada na lista de exceções. Se o firewall estiver desabilitado antes da execução dessa ferramenta, nada adicional será configurado com relação ao firewall.<br /><br /> Se você habilitar o firewall depois de configurar o WS-AT, você precisará executar essa ferramenta novamente e fornecer o número da porta usando esse parâmetro. Se você desabilitar o firewall após a configuração, o WS-AT continuará funcionando sem entrada adicional.|  
|-tempo limite:\<s >|Especifica o tempo limite padrão em segundos. Os valores válidos são de 1 a 3600.|  
|-traceActivity:\<enable&#124;disable>|Habilita ou desabilita o rastreamento de eventos de atividade.|  
|-traceLevel:\<desativar&#124;informações&#124;&#124; de&#124;aviso&#124;crítico de&#124;erro, tudo >}|Especifica o nível de rastreamento.|  
|-tracePII:\<enable&#124;disable>|Habilita ou desabilita o rastreamento de informações de identificação pessoal.|  
|-traceProp:\<enable&#124;disable>|Habilita ou desabilita o rastreamento de eventos de propagação.|  
|-restart|Reinicia o MSDTC para ativar as alterações imediatamente. Se isso não for especificado, as alterações entrarão em vigor quando o MSDTC for reiniciado.|  
|-Mostrar|Exibe as configurações de protocolo WS-AtomicTransaction atuais.|  
|-virtualServer:\<virtualServer>|Especifica o nome do cluster de recursos do DTC.|  
  
## <a name="see-also"></a>Consulte também

- [Usando o WS-AtomicTransaction](./feature-details/using-ws-atomictransaction.md)
- [Configurando o suporte a transações WS-Atomic](./feature-details/configuring-ws-atomic-transaction-support.md)
