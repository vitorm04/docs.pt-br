---
title: Ferramenta de registro de serviço de fluxo de trabalho (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 0a9cd5039c085f82f5507c93ebe0855cc620825d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916831"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a>Ferramenta de registro de serviço de fluxo de trabalho (WFServicesReg.exe)
A ferramenta de registro de serviços de fluxo de trabalho (WFServicesReg. exe) é uma ferramenta autônoma que pode ser usada para adicionar, remover ou reparar os elementos de configuração para os serviços Windows Workflow Foundation (WF).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a>Comentários  
 A ferramenta pode ser encontrada no local [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] de instalação, especificamente,%windir%\Microsoft.NET\Framework\v3.5 ou em%windir%\Microsoft.NET\Framework64\v3.5 em computadores de 64 bits.  
  
 As tabelas a seguir descrevem as opções que podem ser usadas com a ferramenta de registro de serviços de fluxo de trabalho (WFServicesReg. exe).  
  
|Opção|Descrição|  
|------------|-----------------|  
|`/c`|Configura os serviços de fluxo de trabalho do Windows. Usado em cenários de instalação e reparo.|  
|`/r`|Remove a configuração dos serviços de fluxo de trabalho do Windows.|  
|`/v`|Imprimir informações detalhadas (para a configuração ou remoção).|  
|`/m`|Habilita o formato de log MSI.|  
|`/i`|Minimiza a janela quando o aplicativo é executado.|  
  
## <a name="registration"></a>Registro  
 A ferramenta inspeciona o arquivo Web. config e registra o seguinte:  
  
- [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]assemblies de referência.  
  
- Um provedor de compilação para arquivos. xoml.  
  
- Manipuladores HTTP para arquivos. xoml e. Rules.  
  
 A ferramenta inspeciona o arquivo Machine. config e registra as seguintes extensões:  
  
- behaviorExtensions  
  
- bindingElementExtensions  
  
- bindingExtensions  
  
 A ferramenta também registra os seguintes importadores de metadados do cliente:  
  
- policyImporters  
  
- wsdlImporters  
  
 A ferramenta também registra mapas de ferramentas e manipuladores. xoml e. Rules na metabase do IIS.  
  
 Em [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] computadores [!INCLUDE[wxp](../../../includes/wxp-md.md)] e (IIS 5,1 e IIS 6,0), um conjunto de mapas de registro. xoml e. Rules é registrado.  
  
 Em computadores de 64 bits, a ferramenta registra os mapas de bits do `Enable32BitAppOnWin64` modo WOW se a opção estiver habilitada ou mapas de bits `Enable32BitAppOnWin64` 64 nativos se a opção estiver desabilitada.  
  
 No [!INCLUDE[wv](../../../includes/wv-md.md)] e no Windows Server 2008 (IIS 7,0 e superior) computadores, dois conjuntos de manipuladores. xoml e. Rules são registrados: um para o modo integrado e outro para o modo clássico.  
  
 Em computadores de 64 bits, três conjuntos de manipuladores são registrados (independentemente do estado da `Enable32BitAppOnWin64` opção): um para o modo integrado, um para o modo clássico de wow e outro para o modo clássico de 64 bits nativo.  
  
> [!NOTE]
> Ao contrário de ServiceModelreg. exe, o WFServicesReg. exe não permite adicionar, remover ou reparar mapas de chaves ou manipuladores para um site específico. Para obter uma solução alternativa para esse problema, consulte a seção "reparando o ScriptMaps".  
  
## <a name="usage-scenarios"></a>Cenários de uso  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a>Instalando o IIS após a instalação do .NET Framework 3,5  
 Em um [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] computador, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] o é instalado antes da instalação do IIS. Devido à indisponibilidade da metabase do IIS, a instalação de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] é realizada com sucesso sem instalar os mapas de regras. xoml e. Rules.  
  
 Após a instalação do IIS, você pode usar a ferramenta WFServicesReg. exe com `/c` a opção para instalar esses mapas de informações específicos.  
  
### <a name="repairing-the-scriptmaps"></a>Reparando os mapas de chaves  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a>Mapa de site excluído no nó sites  
 Em um [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] computador,. xoml ou. Rules é excluído acidentalmente do nó sites. Isso pode ser reparado executando a ferramenta WFServicesReg. exe com `/c` a opção.  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a>Mapa de site excluído em um local específico  
 Em um [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] computador,. xoml ou. Rules é excluído acidentalmente de um site específico (por exemplo, o site padrão) em vez de no nó sites da Web.  
  
 Para reparar os manipuladores excluídos para um site específico, você deve executar "WFServicesReg. exe/r" para remover manipuladores de todos os sites da Web e, em seguida, executar "WFServicesReg. exe/c" para criar os manipuladores apropriados para todos os sites da Web.  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a>Configurando manipuladores depois de alternar o modo IIS  
 Quando o IIS está no modo de configuração [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] compartilhada e é instalado, a metabase do IIS é configurada em um local compartilhado. Se você alternar o IIS para o modo de configuração não compartilhado, a metabase local não conterá os manipuladores necessários. Para configurar a metabase local corretamente, você pode importar a metabase compartilhada para local ou executar "WFServicesReg. exe/c", que configura a metabase local.
