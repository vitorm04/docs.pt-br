---
title: "Ferramenta de registro de serviço de fluxo de trabalho (WFServicesReg.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f88d5f63ce77eae013e4df995956dc35771a0274
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a>Ferramenta de registro de serviço de fluxo de trabalho (WFServicesReg.exe)
Ferramenta de registro de serviços de fluxo de trabalho (WFServicesReg.exe) é uma ferramenta autônoma que pode ser usada para adicionar, remover ou reparar os elementos de configuração para serviços do Windows Workflow Foundation (WF).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a>Comentários  
 A ferramenta pode ser encontrada no [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] local de instalação, especificamente, % windir%\Microsoft.NET\Framework\v3.5, ou em %windir%\Microsoft.NET\Framework64\v3.5 em máquinas de 64 bits.  
  
 As tabelas a seguir descrevem as opções que podem ser usadas com a ferramenta de registro de serviços de fluxo de trabalho (WFServicesReg.exe).  
  
|Opção|Descrição|  
|------------|-----------------|  
|`/c`|Configurar os serviços de fluxo de trabalho do Windows. Usado na instalação e reparar cenários.|  
|`/r`|Remove a configuração de serviços de fluxo de trabalho do Windows.|  
|`/v`|Imprima informações detalhadas (para configuração ou remoção).|  
|`/m`|Permite que o formato de log MSI.|  
|`/i`|Minimiza a janela quando o aplicativo é executado.|  
  
## <a name="registration"></a>Registro  
 A ferramenta inspeciona o arquivo Web. config e registra o seguinte:  
  
-   [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]assemblies de referência.  
  
-   Um provedor de compilação para arquivos. xoml.  
  
-   Manipuladores HTTP para arquivos xoml e. rules.  
  
 A ferramenta inspeciona o arquivo Machine. config e registra as seguintes extensões:  
  
-   behaviorExtensions  
  
-   bindingElementExtensions  
  
-   bindingExtensions  
  
 A ferramenta também registra os seguintes importadores de metadados do cliente:  
  
-   policyImporters  
  
-   wsdlImporters  
  
 A ferramenta também registra manipuladores e mapas de script. xoml e. Rules na metabase do IIS.  
  
 Em [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../includes/wxp-md.md)] máquinas (IIS 5.1 e [!INCLUDE[iis601](../../../includes/iis601-md.md)]), um conjunto de. xoml e mapas de script. Rules são registrados.  
  
 Em computadores de 64 bits, a ferramenta registra mapas de script de modo WOW se o `Enable32BitAppOnWin64` opção é habilitados ou nativos mapas de script de 64 bits, se o `Enable32BitAppOnWin64` está desativada.  
  
 Em [!INCLUDE[wv](../../../includes/wv-md.md)] e Windows Server 2008 (IIS 7.0 e posterior) máquinas, dois conjuntos de. xoml e. Rules manipuladores registradas: um para modo integrado e outro para o modo clássico.  
  
 Em computadores de 64 bits, três conjuntos de manipuladores registrados (independentemente do estado do `Enable32BitAppOnWin64` alternar): uma para o modo integrado, um para o modo WOW clássico e outro para o modo clássico 64 bits nativo.  
  
> [!NOTE]
>  Ao contrário de ServiceModelreg.exe, WFServicesReg.exe não permite adicionar, remover ou reparar os mapas de script ou manipuladores para um site específico. Para uma solução alternativa para esse problema, consulte a seção "Como reparar os mapas de script".  
  
## <a name="usage-scenarios"></a>Cenários de uso  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a>Instalar o IIS após a instalação do .NET Framework 3.5  
 Em um [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] máquina, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] está instalado antes da instalação do IIS. Devido à indisponibilidade da metabase do IIS, instalação de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] terá êxito sem instalar os scriptmaps. xoml e. rules.  
  
 Depois que o IIS estiver instalado, você pode usar a ferramenta de WFServicesReg.exe com o `/c` switch para instalar esses mapas de script específicos.  
  
### <a name="repairing-the-scriptmaps"></a>Reparar os mapas de script  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a>Mapa de script excluído no nó de Sites da Web  
 Em um [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] máquina,. xoml ou. rules for excluído acidentalmente de nó de Sites da Web. Isso pode ser reparado, executando a ferramenta WFServicesReg.exe com o `/c` alternar.  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a>Mapa de script excluído em um site específico  
 Em um [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] máquina,. xoml ou. rules for excluído acidentalmente de um site específico (por exemplo, o Site padrão), em vez da partir do nó de Sites da Web.  
  
 Para reparar excluídos manipuladores para um site específico, você deve executar "WFServicesReg.exe r" para remover manipuladores de todos os sites da Web, em seguida, execute "WFServicesReg.exe c" para criar os manipuladores apropriados para todos os sites da Web.  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a>Configurando manipuladores depois de alternar o modo IIS  
 Quando o IIS está no modo de configuração compartilhada e [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] é instalado, a metabase do IIS é configurado em um local compartilhado. Se você alternar o IIS para o modo de configuração não compartilhado, a metabase local não conterá os manipuladores necessários. Para configurar a metabase local corretamente, importe a metabase compartilhado no local, ou execute "WFServicesReg.exe /c", que configura a metabase local.
