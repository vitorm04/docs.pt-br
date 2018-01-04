---
title: "Utilitário de configuração de transações WS-Atomic (wsatConfig.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: adb44bfee98d01594c9babcf19e19fbf11ba3878
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>Utilitário de configuração de transações WS-Atomic (wsatConfig.exe)
O utilitário de configuração do WS-AtomicTransaction é usado para definir as configurações básicas do suporte de WS-AtomicTransaction.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Comentários  
 Essa ferramenta de linha de comando pode ser usada para configurar as configurações básicas do WS-AT em apenas um computador local. Se você precisa configurar as configurações em computadores locais e remotos, você deve usar o snap-in do MMC conforme descrito em [configurando suporte a transações WS-Atomic](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
 A ferramenta de linha de comando pode ser encontrada no local de instalação do SDK do Windows, especificamente,  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows comunicação Foundation\wsatConfig.exe  
  
 Se você estiver executando [!INCLUDE[wxp](../../../includes/wxp-md.md)] ou [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], você deve baixar uma atualização antes de executar WsatConfig.exe. Para obter mais informações sobre essa atualização, consulte [atualização para o Commerce Server 2007 (KB912817)](http://go.microsoft.com/fwlink/?LinkId=95340) e [disponibilidade do Windows XP COM+ Hotfix Rollup pacote 13](http://go.microsoft.com/fwlink/?LinkId=95341).  
  
 A tabela a seguir mostra as opções que podem ser usadas com o utilitário de configuração do WS-AtomicTransaction (wsatConfig.exe).  
  
> [!NOTE]
>  Quando você definir um certificado SSL para uma porta selecionada, você substituir o certificado SSL original associado a essa porta se houver.  
  
|Opções|Descrição|  
|-------------|-----------------|  
|-contas:\<conta >|Especifica uma lista separada por vírgulas de contas que podem participar em WS-AtomicTransaction. A validade dessas contas não é verificada.|  
|-accountsCerts:\<thumb > &#124; " Issuer\SubjectName">|Especifica uma lista separada por vírgulas de certificados que podem participar em WS-AtomicTransaction. Os certificados são indicados pela impressão digital ou pelo par Issuer\SubjectName. Use {EMPTY} para o nome da entidade se ela estiver vazia.|  
|-endpointCert: < máquina &#124; \<thumb > &#124; " Issuer\SubjectName">|Usa o certificado da máquina ou outro certificado local de ponto de extremidade especificado pela impressão digital ou pelo par Issuer\SubjectName. Usa {EMPTY} para o nome da entidade se ela estiver vazia.|  
|-maxTimeout:\<s >|Especifica o tempo limite máximo em segundos. Os valores válidos são de 0 a 3600.|  
|-rede:\<Habilitar &#124; desabilitar >|Habilita ou desabilita o suporte de rede WS-AtomicTransaction.|  
|-porta:\<portNum >|Define a porta HTTPS para WS-AtomicTransaction.<br /><br /> Se você já tiver ativado o firewall antes de executar essa ferramenta, a porta será registrada automaticamente na lista de exceções. Se o firewall estiver desabilitado antes de executar essa ferramenta, nenhuma tarefa adicional é configurada sobre o firewall.<br /><br /> Se você habilitar o firewall após a configuração WS-AT, você precisa executar essa ferramenta novamente e forneça o número de porta que o uso desse parâmetro. Se você desabilitar o firewall depois de configurar, WS-AT continuará a funcionar sem entrada adicional.|  
|tempo - limite:\<s >|Especifica o tempo limite padrão em segundos. Os valores válidos são de 1 a 3600.|  
|-traceActivity:\<Habilitar &#124; desabilitar >|Habilita ou desabilita o rastreamento de eventos de atividade.|  
|-traceLevel:\<Off &#124; Erro &#124; Crítico &#124; Aviso &#124; informações &#124; Verbose &#124; Todos os >}|Especifica o nível de rastreamento.|  
|-tracePII:\<Habilitar &#124; desabilitar >|Habilita ou desabilita o rastreamento de informações de identificação pessoal.|  
|-traceProp:\<Habilitar &#124; desabilitar >|Habilita ou desabilita o rastreamento de eventos de propagação.|  
|-reiniciar|Reinicia o MSDTC para ativar as alterações imediatamente. Se não for especificado, as alterações entram em vigor quando o MSDTC é reiniciado.|  
|-Mostrar|Exibe as configurações de protocolo WS-AtomicTransaction atuais.|  
|-Servidor_virtual:\<Servidor_virtual >|Especifica o nome do cluster de recurso DTC.|  
  
## <a name="see-also"></a>Consulte também  
 [Usando o WS-AtomicTransaction](../../../docs/framework/wcf/feature-details/using-ws-atomictransaction.md)  
 [Configurando o suporte a transações WS-Atomic](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
