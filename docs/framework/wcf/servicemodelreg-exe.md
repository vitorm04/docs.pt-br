---
title: Ferramenta de registro de ServiceModel (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 5fab1a356cd035ed006bfe90d713e179907e0137
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051774"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>Ferramenta de registro de ServiceModel (ServiceModelReg.exe)
Essa ferramenta de linha de comando fornece a capacidade de gerenciar o registro de componentes do WCF e WF em um único computador. Em circunstâncias normais não deve precisar usar essa ferramenta como o WCF e componentes do WF são configuradas quando instalado. Mas se você estiver tendo problemas com a ativação de serviço, você pode tentar registrar os componentes usando essa ferramenta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>Comentários  
 A ferramenta pode ser encontrada no seguinte local:  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
> [!NOTE]
>  Quando a ferramenta de registro de ServiceModel é executada no [!INCLUDE[wv](../../../includes/wv-md.md)], o **recursos do Windows** caixa de diálogo pode não refletir que o **Windows Communication Foundation HTTP Activation** opção sob **Microsoft .NET Framework 3.0** está ativado. O **recursos do Windows** caixa de diálogo pode ser acessada clicando **iniciar**, em seguida, clique em **execute** e, em seguida, digitando **OptionalFeatures**.  
  
 As tabelas a seguir descrevem as opções que podem ser usadas com ServiceModelReg.exe.  
  
|Opção|Descrição|  
|------------|-----------------|  
|`-ia`|Instala todos os componentes do WCF e WF.|  
|`-ua`|Desinstala todos os componentes do WCF e WF.|  
|`-r`|Repara todos os componentes do WCF e WF.|  
|`-i`|Instala os componentes do WCF e WF especificados com – c.|  
|`-u`|Desinstala o WCF e WF componentes especificados com – c.|  
|`-c`|Instala ou desinstala um componente:<br /><br /> -httpnamespace – reserva de Namespace HTTP<br />serviço de compartilhamento de porta - tcpportsharing – TCP<br />serviço de ativação - tcpactivation – TCP (não tem suportado no .NET 4 Client Profile)<br />serviço - namedpipeactivation – ativação de pipe nomeado (não tem suportado no .NET 4 Client Profile<br />serviço de ativação - msmqactivation – MSMQ (não tem suportado no .NET 4 Client Profile<br />os manifestos de rastreamento de eventos - etw – ETW (Windows Vista ou posterior)|  
|`-q`|Modo silencioso (log de erros de exibição única)|  
|`-v`|modo detalhado.|  
|`-nologo`|Suprime a mensagem de copyright e de banner.|  
|`-?`|Exibe o texto de ajuda|  
  
## <a name="fixing-the-fileloadexception-error"></a>Corrigir o erro FileLoadException  
 Se você instalou versões anteriores do WCF em seu computador, você poderá receber um `FileLoadFoundException` erro ao executar a ferramenta ServiceModelReg para registrar uma nova instalação. Isso pode acontecer mesmo que você manualmente tiver removido arquivos de instalação anterior, mas intactos as configurações de Machine. config.  
  
 A mensagem de erro é semelhante ao seguinte.  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 Você deve observar da mensagem de erro que o assembly System. ServiceModel versão 2.0.0.0 foi instalado por uma versão inicial do Customer Technology Preview (CTP). A versão atual do assembly System. ServiceModel liberado é 3.0.0.0 em vez disso. Portanto, esse problema é encontrado quando você deseja instalar a versão oficial do WCF em um computador em que uma versão inicial do CTP do WCF foi instalada, mas não completamente desinstalada.  
  
 ServiceModelReg.exe não é possível limpar as entradas da versão anterior, nem pode ele entradas de registro da nova versão. A única solução alternativa é editar manualmente o Machine. config. Você pode localizar esse arquivo no seguinte local.  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 Se você estiver executando o WCF em um computador de 64 bits, você também deve editar o mesmo arquivo neste local.  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 Localize todos os nós XML nesse arquivo que se referem a "System. ServiceModel, Version = 2.0.0.0", exclua-os e nós filho. Salve o arquivo e execute novamente ServiceModelReg.exe resolve esse problema.  
  
## <a name="examples"></a>Exemplos  
 Os exemplos a seguir mostram como usar as opções mais comuns da ferramenta ServiceModelReg.exe.  
  
```  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
