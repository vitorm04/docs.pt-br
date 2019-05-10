---
title: Ferramenta de registro de serviço de fluxo de trabalho (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: da377e865258169bdca16cfb0db3f8612d4e0f0d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613049"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a>Ferramenta de registro de serviço de fluxo de trabalho (WFServicesReg.exe)
Ferramenta de registro de serviços de fluxo de trabalho (WFServicesReg.exe) é uma ferramenta autônoma que pode ser usada para adicionar, remover ou reparar os elementos de configuração para serviços do Windows Workflow Foundation (WF).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a>Comentários  
 A ferramenta pode ser encontrada na [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] local de instalação, especificamente, % windir%\Microsoft.NET\Framework\v3.5, ou em %windir%\Microsoft.NET\Framework64\v3.5 em máquinas de 64 bits.  
  
 As tabelas a seguir descrevem as opções que podem ser usadas com a ferramenta de registro de serviços de fluxo de trabalho (WFServicesReg.exe).  
  
|Opção|Descrição|  
|------------|-----------------|  
|`/c`|Configura os serviços de fluxo de trabalho do Windows. Usado na instalação e reparar cenários.|  
|`/r`|Remove a configuração de serviços de fluxo de trabalho do Windows.|  
|`/v`|Informações detalhadas (para configuração ou remoção) de impressão.|  
|`/m`|Permite que o formato de log MSI.|  
|`/i`|Minimiza a janela quando o aplicativo é executado.|  
  
## <a name="registration"></a>Registro  
 A ferramenta inspeciona o arquivo Web. config e registra o seguinte:  
  
- [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] assemblies de referência.  
  
- Um provedor de build para arquivos. xoml.  
  
- Manipuladores HTTP para arquivos. xoml e. rules.  
  
 A ferramenta inspeciona o arquivo Machine. config e registra as seguintes extensões:  
  
- behaviorExtensions  
  
- bindingElementExtensions  
  
- bindingExtensions  
  
 A ferramenta também registra os importadores de metadados do cliente seguintes:  
  
- policyImporters  
  
- wsdlImporters  
  
 A ferramenta também registra manipuladores e mapas de script. xoml e. Rules na metabase do IIS.  
  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../includes/wxp-md.md)] máquinas (o IIS 5.1 e [!INCLUDE[iis601](../../../includes/iis601-md.md)]), um definido. xoml e mapas de script. Rules são registrados.  
  
 Em computadores de 64 bits, a ferramenta registra mapas de script de modo WOW se o `Enable32BitAppOnWin64` opção é habilitados ou nativos mapas de script de 64 bits, se o `Enable32BitAppOnWin64` está desativada.  
  
 Em [!INCLUDE[wv](../../../includes/wv-md.md)] e Windows Server 2008 (IIS 7.0 e posterior) máquinas, dois conjuntos de xoml e. Rules manipuladores são registradas: um para modo integrado e outro para o modo clássico.  
  
 Em computadores de 64 bits, três conjuntos de manipuladores registrados (independentemente do estado do `Enable32BitAppOnWin64` alternar): uma para o modo integrado, um para o modo WOW clássico e outro para o modo de clássico de 64 bits nativo.  
  
> [!NOTE]
>  Ao contrário de ServiceModelreg.exe, WFServicesReg.exe permite adicionar, remover ou reparando mapas de script ou manipuladores para um determinado site. Para uma solução alternativa para esse problema, consulte a seção "Como reparar os mapas de script".  
  
## <a name="usage-scenarios"></a>Cenários de uso  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a>Instalando o IIS após a instalação do .NET Framework 3.5  
 Em um [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] está instalado antes da instalação do IIS. Devido à indisponibilidade da metabase do IIS, instalação de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] terá êxito sem instalar os mapas de script. xoml e. rules.  
  
 Depois que o IIS estiver instalado, você pode usar a ferramenta WFServicesReg.exe com o `/c` switch para instalar esses mapas de script específicos.  
  
### <a name="repairing-the-scriptmaps"></a>Reparar os mapas de script  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a>Mapa de script excluído sob o nó Sites da Web  
 Em um [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] máquina,. xoml ou. rules for excluído acidentalmente a partir do nó de Sites da Web. Isso pode ser reparado, executando a ferramenta WFServicesReg.exe com o `/c` alternar.  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a>Mapa de script excluído em um site específico  
 Em um [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] máquina,. xoml ou. rules for acidentalmente excluído de um site específico (por exemplo, o Site padrão) em vez do nó de Sites da Web.  
  
 Para reparar excluídos manipuladores para um determinado site, você deve executar "WFServicesReg.exe r" para remover manipuladores de todos os sites da Web, em seguida, execute "c WFServicesReg.exe" para criar os manipuladores apropriados para todos os sites da Web.  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a>Configurando manipuladores depois de alternar o modo de IIS  
 Quando o IIS está no modo de configuração compartilhada e [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] é instalado, a metabase do IIS é configurado em um local compartilhado. Se você alternar o IIS para o modo de configuração não compartilhado, metabase local não conterá os manipuladores de necessários. Para configurar corretamente a metabase local, importe a metabase compartilhado no local ou de execução "WFServicesReg.exe/c", que configura a metabase do local.
