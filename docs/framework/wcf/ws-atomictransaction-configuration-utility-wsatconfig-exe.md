---
title: Utilitário de configuração de transações WS-Atomic (wsatConfig.exe)
ms.date: 03/30/2017
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
ms.openlocfilehash: b4c2bb2d9c81b6ab3afc783d1188de7664e01566
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741412"
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>Utilitário de configuração de transações WS-Atomic (wsatConfig.exe)
O utilitário de configuração do WS-AtomicTransaction é usado para definir as configurações básicas do suporte de WS-AtomicTransaction.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Comentários  
 Essa ferramenta de linha de comando pode ser usada para configurar as configurações básicas de WS-AT em uma máquina local apenas. Se você precisa definir as configurações nos computadores locais e remoto, você deve usar o snap-in do MMC conforme descrito em [Configurando o suporte a transações WS-Atomic](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
 A ferramenta de linha de comando pode ser encontrada no local de instalação do SDK do Windows, especificamente,  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\wsatConfig.exe  
  
 Se você estiver executando [!INCLUDE[wxp](../../../includes/wxp-md.md)] ou [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], você deve baixar uma atualização antes de executar WsatConfig.exe. Para obter mais informações sobre essa atualização, consulte [atualizar para o Commerce Server 2007 (KB912817)](https://go.microsoft.com/fwlink/?LinkId=95340) e [disponibilidade do Windows XP COM+ Hotfix Rollup pacote 13](https://go.microsoft.com/fwlink/?LinkId=95341).  
  
 A tabela a seguir mostra as opções que podem ser usadas com o utilitário de configuração do WS-AtomicTransaction (wsatConfig.exe).  
  
> [!NOTE]
>  Quando você definir um certificado SSL para uma porta selecionada, você pode substituir o certificado SSL original associado com essa porta, se houver um.  
  
|Opções|Descrição|  
|-------------|-----------------|  
|-accounts:\<account,>|Especifica uma lista separada por vírgulas de contas que podem participar em WS-AtomicTransaction. Não é verificada a validade dessas contas.|  
|-accountsCerts:\<thumb>&#124;"Issuer\SubjectName",>|Especifica uma lista separada por vírgulas de certificados que podem participar em WS-AtomicTransaction. Os certificados são indicados por impressão digital ou pelo par Issuer\SubjectName. Use {EMPTY} para o nome da entidade se ela estiver vazia.|  
|-endpointCert:<machine&#124;\<thumb>&#124;"Issuer\SubjectName">|Usa o certificado do computador ou outro certificado de ponto de extremidade local especificado pela impressão digital ou par Issuer\SubjectName. Usa {EMPTY} para o nome da entidade se ela estiver vazia.|  
|-maxTimeout:\<sec>|Especifica o tempo limite máximo em segundos. Os valores válidos são de 0 a 3600.|  
|-network:\<enable&#124;disable>|Habilita ou desabilita o suporte de rede WS-AtomicTransaction.|  
|-port:\<portNum>|Define a porta HTTPS para WS-AtomicTransaction.<br /><br /> Se você já tiver habilitado o firewall antes de executar essa ferramenta, a porta é registrada automaticamente na lista de exceções. Se o firewall está desabilitado antes de executar essa ferramenta, nada mais é configurado sobre o firewall.<br /><br /> Se você habilitar o firewall depois de configurar WS-AT, você precisa executar essa ferramenta novamente e forneça o número de porta que o uso desse parâmetro. Se você desabilitar o firewall depois de configurar, WS-AT continua a funcionar sem entrada adicional.|  
|-timeout:\<sec>|Especifica o tempo limite padrão em segundos. Os valores válidos são de 1 a 3600.|  
|-traceActivity:\<enable&#124;disable>|Habilita ou desabilita o rastreamento de eventos de atividade.|  
|-traceLevel:\<Off&#124;erro&#124;crítico&#124;aviso&#124;informações&#124; detalhado&#124;todos os >}|Especifica o nível de rastreamento.|  
|-tracePII:\<enable&#124;disable>|Habilita ou desabilita o rastreamento de informações de identificação pessoal.|  
|-traceProp:\<enable&#124;disable>|Habilita ou desabilita o rastreamento de eventos de propagação.|  
|-reiniciar|Reinicia o MSDTC para ativar as alterações imediatamente. Se não for especificado, as alterações entram em vigor quando o MSDTC é reiniciado.|  
|-Mostrar|Exibe as configurações do protocolo WS-AtomicTransaction atuais.|  
|-virtualServer:\<virtualServer>|Especifica o nome do cluster de recurso DTC.|  
  
## <a name="see-also"></a>Consulte também
- [Usando o WS-AtomicTransaction](../../../docs/framework/wcf/feature-details/using-ws-atomictransaction.md)
- [Configurando o suporte a transações WS-Atomic](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
