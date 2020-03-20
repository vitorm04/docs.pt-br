---
title: Ferramenta de registro de ServiceModel (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: a6f65ccc6caa0a7e496e7de8c83259ab48903753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183101"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>Ferramenta de registro de ServiceModel (ServiceModelReg.exe)
Esta ferramenta de linha de comando fornece a capacidade de gerenciar o registro de componentes WCF e WF em uma única máquina. Em circunstâncias normais, você não deve precisar usar esta ferramenta, pois os componentes WCF e WF são configurados quando instalados. Mas se você estiver tendo problemas com a ativação do serviço, você pode tentar registrar os componentes usando esta ferramenta.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>Comentários  
 A ferramenta pode ser encontrada no seguinte local:  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
> [!NOTE]
> Quando a ferramenta de registro ServiceModel é executada no Windows Vista, a caixa de diálogo Recursos do **Windows** pode não refletir que a opção **de ativação HTTP** da Windows Communication Foundation em **Microsoft .NET Framework 3.0** esteja ativada. A caixa de diálogo Recursos do **Windows** pode ser acessada clicando **em Iniciar,** depois clique **em Executar** e, em seguida, digitando **Opcionais .**  
  
 As tabelas a seguir descrevem as opções que podem ser usadas com ServiceModelReg.exe.  
  
|Opção|Descrição|  
|------------|-----------------|  
|`-ia`|Instala todos os componentes WCF e WF.|  
|`-ua`|Desinstala todos os componentes WCF e WF.|  
|`-r`|Repara todos os componentes WCF e WF.|  
|`-i`|Instala componentes WCF e WF especificados com –c.|  
|`-u`|Desinstala os componentes WCF e WF especificados com –c.|  
|`-c`|Instala ou desinstala um componente:<br /><br /> - httpnamespace - HTTP Namespace Reservation<br />- tcpportsharing – Serviço de compartilhamento de portas TCP<br />- ativação tcp – serviço de ativação TCP (sem suporte no Perfil do Cliente .NET 4)<br />- nomeativação de tubos – Serviço de ativação de tubulação nomeado (sem suporte no Perfil do Cliente .NET 4<br />- msmqactivation – Serviço de ativação MSMQ (sem suporte no Perfil do Cliente .NET 4<br />- etw – ETW event tracing manifests (Windows Vista ou posterior)|  
|`-q`|Modo silencioso (apenas registro de erro de exibição)|  
|`-v`|Modo verbose.|  
|`-nologo`|Suprime os direitos autorais e a mensagem de banner.|  
|`-?`|Exibe texto de ajuda|  
  
## <a name="fixing-the-fileloadexception-error"></a>Corrigindo o erro FileLoadException  
 Se você instalou versões anteriores do WCF em sua máquina, você pode obter um `FileLoadFoundException` erro ao executar a ferramenta ServiceModelReg para registrar uma nova instalação. Isso pode acontecer mesmo se você tiver removido manualmente arquivos da instalação anterior, mas deixou as configurações da máquina.config intactas.  
  
 A mensagem de erro é semelhante à seguinte.  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 Você deve observar a partir da mensagem de erro que o conjunto System.ServiceModel Versão 2.0.0.0 foi instalado por uma versão inicial da Visualização de Tecnologia do Cliente (CTP). A versão atual do conjunto System.ServiceModel lançada é 3.0.0.0. Portanto, este problema é encontrado quando você deseja instalar a versão oficial do WCF em uma máquina onde uma versão ctp inicial do WCF foi instalada, mas não completamente desinstalada.  
  
 ServiceModelReg.exe não pode limpar entradas de versão anteriores, nem pode registrar as entradas da nova versão. A única solução é editar manualmente machine.config. Você pode localizar este arquivo no seguinte local.  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 Se você estiver executando o WCF em uma máquina de 64 bits, você também deve editar o mesmo arquivo neste local.  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 Localize quaisquer nós XML neste arquivo que se referem a "System.ServiceModel, Version=2.0.0.0", exclua-os e quaisquer nós de criança. Salvar o arquivo e executar o ServiceModelReg.exe resolve esse problema.  
  
## <a name="examples"></a>Exemplos  
 Os exemplos a seguir mostram como usar as opções mais comuns da ferramenta ServiceModelReg.exe.  
  
```console  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
