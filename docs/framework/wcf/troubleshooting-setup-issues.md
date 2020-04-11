---
title: Solucionando problemas de instalação
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 2cd9ced4f0780b1a6f63e4a5833e20ac91870121
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121588"
---
# <a name="troubleshoot-setup-issues"></a>Problemas de configuração de solução de problemas

Este artigo descreve como solucionar problemas da Windows Communication Foundation (WCF) para configurar problemas.  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>Algumas chaves do Registro do Windows Communication Foundation não são reparadas executando uma operação de reparo do MSI no .NET Framework 3.0  
 Se você excluir algumas das seguintes chaves do Registro:  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0  
  
 As teclas não serão recriadas se você executar o reparo usando o instalador .NET Framework 3.0 lançado a partir do applet **Adicionar/Remover Programas** no **Painel de Controle**. Para recriar corretamente essas chaves, o usuário deverá desinstalar e reinstalar o .NET Framework 3.0.  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a>O WMI Service Corruption bloqueia a instalação do provedor WMI do Windows Communication Foundation durante a instalação do pacote do .NET Framework 3.0  
 O WMI Service Corruption pode bloquear a instalação do provedor WMI do Windows Communication Foundation. Durante a instalação, o instalador do Windows Communication Foundation não é capaz de registrar o arquivo .mof do WCF usando o componente mofcomp.exe. Veja a seguir uma lista de sintomas:  
  
1. A instalação do .NET Framework 3.0 é concluída com sucesso, mas o provedor WMI do WCF não é registrado.  
  
2. Um evento de erro aparece no log de eventos do aplicativo que faz referência aos problemas registrando o provedor WMI para WCF ou executando mofcomp.exe.  
  
3. O arquivo de log de configuração chamado dd_wcf_retCA* no diretório %temp% do usuário contém referências a falhas para registrar o provedor WMI do WCF.  
  
4. Uma exceção como a seguinte pode ser listada no log de eventos ou no arquivo de log de rastreamento de configuração:  
  
     ServiceModelReg [11:09:59:046]: System.ApplicationException: Unexpected result 3 executing E:\WINDOWS\system32\wbem\mofcomp.exe with "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof"  
  
     ou:  
  
     ServiceModelReg [07:19:33:843]: System.TypeInitializationException: The type initializer for 'System.Management.ManagementPath' threw an exception. ---> System.Runtime.InteropServices.COMException (0x80040154): Recuperando a fábrica da classe COM para componente com CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} falhou devido ao seguinte erro: 80040154.  
  
     ou:  
  
     ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: Could not load file or assembly 'C:\WINDOWS\system32\wbem\mofcomp.exe' or one of its dependencies. O sistema não pode encontrar o arquivo especificado.  
  
     Nome de arquivo: 'C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 As etapas a seguir devem ser seguidas para resolver o problema descrito anteriormente.  
  
1. Execute o [Utilitário de Diagnóstico WMI](https://www.microsoft.com/download/details.aspx?id=7684) para reparar o serviço WMI. Para obter mais informações sobre o uso desta ferramenta, consulte [WMI Diagnosis Utility](https://docs.microsoft.com/previous-versions/tn-archive/ff404265(v%3dmsdn.10)).  
  
 Reparar a instalação do .NET Framework 3.0 usando o applet **Adicionar/Remover Programas** localizado no **Painel de Controle**ou desinstalar/reinstalar o .NET Framework 3.0.  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a>Reparar o .NET Framework 3.0 após a instalação do .NET Framework 3.5 remove os elementos de configuração introduzidos pelo .NET Framework 3.5 em machine.config  
 Se você fizer um reparo do .NET Framework 3.0 depois de instalar o .NET Framework 3.5, os elementos de configuração introduzidos pelo .NET Framework 3.5 na machine.config serão removidos. No entanto, o web.config permanecerá intacto. A solução é reparar o .NET Framework 3.5 depois disso via ARP, ou usar a Ferramenta `/c` de Registro de Serviços do [WorkFlow (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) com o switch.  
  
 A ferramenta de [registro de serviço sinfemio (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) pode ser encontrada em %windir%\Microsoft.NET\framework\v3.5\ ou %windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>Configure o IIS corretamente para WCF/WF Webhost após instalar o .NET Framework 3.5  
 Quando a instalação do .NET Framework 3.5 falha em configurar configurações adicionais de Configuração IIS relacionadas ao WCF, ela registra um erro no registro de instalação e continua. Qualquer tentativa de executar aplicativos do WorkflowServices falhará, porque os parâmetros de configuração necessários estão faltando. Por exemplo, carregar xoml ou o serviço de regras pode falhar.  
  
 Para contornar esse problema, use a Ferramenta de Registro de Serviços `/c` do [WorkFlow (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) com o switch para configurar corretamente mapas de script IIS na máquina. A ferramenta de [registro de serviço sinfemio (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) pode ser encontrada em %windir%\Microsoft.NET\framework\v3.5\ ou %windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a>Não foi possível carregar o tipo 'System.ServiceModel.Activation.HttpModule' do conjunto 'System.ServiceModel, Versão 3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
 Esse erro ocorre se o .NET Framework 4 estiver instalado e, em seguida, a ativação DO WCF HTTP estiver ativada. Para resolver o problema, execute a seguinte linha de comando de dentro do Prompt de comando do desenvolvedor para o Visual Studio:  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>Confira também

- [Instruções de configuração](./samples/set-up-instructions.md)
